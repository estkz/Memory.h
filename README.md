# Memory.h
The Memory.h class is a toolset for accessing and manipulating game memory, enabling tasks like process identification, module addressing, memory reading, and writing.

To use these functions, consider this example involving the game Assault Cube and its module "ac_client.exe":

```c++
// Offsets Example.
constexpr auto localPlayer = 0x17E0A8;
constexpr auto ptrHealth = 0xEC;

// Setup the foundation for your memory manipulation operations.
Memory memory{ "ac_client.exe" };

// Define the ModuleBaseAddress
const auto moduleBase = memory.GetModuleAddress("ac_client.exe");

// Example of how to read and write the health address using local player and an offset to the health value:
const auto localPlayerPtr = memory.Read<std::uintptr_t>(moduleBase + localPlayer);
const auto healthAddress = localPlayerPtr + ptrHealth;

// Example of a simple god mode hack.
const int newHealth = 1337;
memory.Write<int>(healthAddress, newHealth);
ImGui::Text("Health: %d", memory.Read<int>(healthAddress)); // I'm using the ImGui Framework to display the value stored in the health address, but you can use std::cout if you prefer.
```

For a comprehensive breakdown of each function's purpose and functionality, please refer to my Discord server: https://discord.gg/YuCxC7n9Zm
