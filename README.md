# Memory.h
The "Memory.h" class is a toolset for accessing and manipulating game memory, enabling tasks like process identification, module addressing, memory reading, and writing.

To use these functions, consider this example involving the game Assault Cube and its module "ac_client.exe":

Memory memory{ "ac_client.exe" };
const auto moduleBase = memory.GetModuleAddress("ac_client.exe");

// Example of how to read and write the health address using local player and an offset to the health value:
```c++
// Offsets Example
constexpr auto localPlayer = 0x17E0A8;
constexpr auto ptrHealth = 0xEC;

const auto localPlayerPtr = memory.Read<std::uintptr_t>(moduleBase + localPlayer);
const auto healthAddress = localPlayerPtr + ptrHealth;

const int newHealth = 1337;
memory.Write<int>(healthAddress, newHealth);
ImGui::Text("Health: %d", memory.Read<int>(healthAddress)); // I'm using the ImGui Framework to display the value stored in the health address, but you can use std::cout if you prefer.
```
