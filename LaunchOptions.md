# What is a launch option?

A launch option or rather a launch flag, is a flag you pass to proton to change its behaviour. You can think of it as an on/off switch for various features and behaviours that Proton has available.

In general definition:

(Quoting [Quora](https://www.quora.com/What-is-a-flag-in-programming) )
"In programming, a flag is a variable or a value that acts as a signal for a certain condition or behavior. Flags are commonly used to control the flow of a program, to indicate the presence or absence of a feature, or to trigger specific actions based on certain conditions. For example, a flag variable could be used to indicate whether a certain option is enabled or disabled in a program."

## How to use a launch option

To use a launch option for a game on Steam, right click on the game you want to set a launch option for, click on ``Properties`` and under ``General`` there should be a section called ``Launch Options``

## Launch option list

There are a lot of launch options and I am not sure If I can list them all here, but I will add them as time goes on and I discover more. Keep in mind these are launch options used to achieve behaviours with Proton for performance improvements, functionality, debugging and et cetera.

**PROTON_USE_WINED3D=1**: Runs games with OpenGL instead of Vulkan. This is especially useful for old GPUs without Vulkan support.

**PROTON_NO_ESYNC=1**: Turns off ESync.

**PROTON_NO_FSYNC=1**: Turns off FSync

**PROTON_NO_D3D11=1**: Disables DirectX11 (d3d11) for games that can fall back to DirectX9 (d3d9). The usecase for this is for older GPUs or to get better performance.*This will not work for all games, nor all games running with DirectX11.*

**PROTON_NO_D3D10=1**: Disables DirectX10 (d3d10) for games that can fall back to DirectX9 (d3d9). The usecase for this is for older GPUs or to get better performance. *This will not work for all games, nor all games running with DirectX11.*

**PROTON_HIDE_NVIDIA_GPU=1**: Force Nvidia GPUs to always be reported as AMD GPUs. Some games require this if they depend on Windows-only Nvidia driver functionality.

**DRI_PRIME=1**: Forces Proton to use your dedicated AMD GPU. Games may default to using your integrated gpu (iGPU) on (for example) a laptop or a hybrid setup with 1 iGPU and 1 dedicated GPU (dGPU).

**__NV_PRIME_RENDER_OFFLOAD=1**: Forces Proton to use your dedicated Nvidia GPU for Vulkan games. Games may default to using your integrated gpu (iGPU) on (for example) a laptop or a hybrid setup with 1 iGPU and 1 dedicated GPU (dGPU).

**__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia**: Forces Proton to use your dedicated Nvidia GPU for OpenGL games. Games may default to using your integrated gpu (iGPU) on (for example) a laptop or a hybrid setup with 1 iGPU and 1 dedicated GPU (dGPU).

**VK_INSTANCE_LAYERS=VK_LAYER_MESA_overlay**: Enables the Mesa HUD overlay. The Mesa HUD displays GPU name, driver version, FPS, and frametime *NOTE: (This HUD only works only with Vulkan games and games running through DXVK, and it only works with AMD and Intel GPUs)*.

**DXVK_HUD=<option>**: Enables the DXVK HUD to display useful information like fps, frametime and et cetera. Only works with Games running with DXVK (or more familiarly, games running through the translation of DirectX9, DirectX10 and Direct11). Currently available `option`s are: 
- `devinfo`: Displays the name of the GPU and the driver version.
- `fps`: Shows the current frame rate.
- `frametimes`: Shows a frame time graph.
- `submissions`: Shows the number of command buffers submitted per frame.
- `drawcalls`: Shows the number of draw calls and render passes per frame.
- `pipelines`: Shows the total number of graphics and compute pipelines.
- `descriptors`: Shows the number of descriptor pools and descriptor sets.
- `memory`: Shows the amount of device memory allocated and used.
- `gpuload`: Shows estimated GPU load. May be inaccurate.
- `version`: Shows DXVK version.
- `api`: Shows the D3D feature level used by the application.
- `cs`: Shows worker thread statistics.
- `compiler`: Shows shader compiler activity
- `samplers`: Shows the current number of sampler pairs used *[DirectX9 (D3D9) Only]*
- `scale=x`: Scales the HUD by a factor of `x` (e.g. `1.5`)
- `opacity=y`: Adjusts the HUD opacity by a factor of `y` (e.g. `0.5`, `1.0` being fully opaque).

Additionally, `DXVK_HUD=1` has the same effect as `DXVK_HUD=devinfo,fps`, and `DXVK_HUD=full` enables all available HUD elements.

**DXVK_FRAME_RATE=<number>**: Limits the FPS to the amount specified in the `number` variable. A value of `0` uncaps the frame rate, while any positive value will limit rendering to the given number of frames per second. Alternatively, the configuration file can be used.

### Program specific options

These options are not exclusively related to Proton and **require the user to install the respective programs referenced in the launch option for them to function**. These options are referenced around forums and websites like [ProtonDB](https://www.protondb.com/) related to Proton.

**mangohud**: Enables the MangoHud overlay. MangoHud is a Vulkan and OpenGL overlay for monitoring FPS, temperatures, CPU/GPU load and more. Similar to [MSi Afterburner](https://www.msi.com/Landing/afterburner/graphics-cards) on Windows. Main repo: https://github.com/flightlessmango/MangoHud

**ENABLE_VKBASALT=1**: Enables vkBasalt. vkBasalt is a vulkan post processing layer for linux. It is similar to ReShade. Main repo: https://github.com/DadSchoorse/vkBasalt

**gamemoderun**: Enables gamemode. `gamemode` is a program that "optimizes linux performance on demand". It does this by giving your CPU instructions to prioritize the processing of data from the specified program. This may lead to your desktop being slower while the game is running. Main repo: https://github.com/FeralInteractive/gamemode

### Debugging options

Debugging options are not useful outside of debugging purposes, so they have no practical use for the average Proton user.

**DXVK_STATE_CACHE=<option>**: DXVK caches pipeline state by default, so that shaders can be recompiled ahead of time on subsequent runs of an application, even if the driver's own shader cache got invalidated in the meantime. This cache is enabled by default, and generally reduces stuttering. Available valid ``option``s are: 
  - `disable`: Disables the cache entirely.
  - `reset`: Clears the cache file.

-**DXVK_STATE_CACHE_PATH=<directory>** Specifies a directory where to put the cache files. Defaults to the current working directory of the application.

**VK_INSTANCE_LAYERS=VK_LAYER_KHRONOS_validation**: Enables Vulkan debug layers. Highly recommended for troubleshooting rendering issues and driver crashes. Requires the Vulkan SDK to be installed on the host system.

**DXVK_LOG_LEVEL=none|error|warn|info|debug**: Controls message logging.

**DXVK_LOG_PATH=/some/directory**: Changes path where log files are stored. Set to `none` to disable log file creation entirely, without disabling logging.

**DXVK_DEBUG=markers|validation**: Enables use of the `VK_EXT_debug_utils` extension for translating performance event markers, or to enable Vulkan validation, respecticely.

**DXVK_CONFIG_FILE=/xxx/dxvk.conf**: Sets path to the configuration file.

**DXVK_CONFIG="dxgi.hideAmdGpu = True; dxgi.syncInterval = 0"**: Can be used to set config variables through the environment instead of a configuration file using the same syntax. `;` is used as a seperator

