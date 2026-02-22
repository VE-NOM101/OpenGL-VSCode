Here’s a clear step-by-step guide to run an OpenGL project using VS Code (Windows focus, since most students use it).
1️⃣ Install Required Software
✅ Install a C/C++ Compiler
Install MinGW-w64 (GCC for Windows)
Add bin folder to PATH
Check:
g++ --version
✅ Install VS Code
Install Visual Studio Code
Install extensions:
C/C++ (by Microsoft)
Code Runner (optional)
2️⃣ Download OpenGL Libraries
You need these three:

🔹 OpenGL**
(Already included with Windows — no extra install)

🔹 GLFW**
Download from: https://www.glfw.org
Extract:
include/GLFW
lib-mingw-w64
🔹 GLAD**
Generate from: https://glad.dav1d.de
Language: C/C++
API: OpenGL
Profile: Core
Version: 3.3+
Extract:
include/glad
src/glad.c
3️⃣ Project Folder Structure
OpenGL_Project/
│
├── include/
│   ├── glad/
│   └── GLFW/
│
├── lib/
│   └── libglfw3.a
│
├── src/
│   ├── main.cpp
│   └── glad.c
│
└── build/
4️⃣ Sample main.cpp
#include <glad/glad.h>
#include <GLFW/glfw3.h>
#include <iostream>

int main() {
    glfwInit();
    GLFWwindow* window = glfwCreateWindow(800, 600, "OpenGL", NULL, NULL);
    glfwMakeContextCurrent(window);

    if (!gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)) {
        std::cout << "Failed to initialize GLAD\n";
        return -1;
    }

    while (!glfwWindowShouldClose(window)) {
        glClear(GL_COLOR_BUFFER_BIT);
        glfwSwapBuffers(window);
        glfwPollEvents();
    }

    glfwTerminate();
    return 0;
}
5️⃣ Compile & Run (Terminal in VS Code)
Open VS Code terminal in project folder and run:

g++ src/main.cpp src/glad.c -Iinclude -Llib -lglfw3 -lopengl32 -lgdi32 -o app
Then run:

app
✔️ A window should appear.
6️⃣ Common Errors & Fixes
ErrorSolutionglad.h not foundCheck -Iincludeundefined reference to glfwCheck -Llib -lglfw3Window not openingCall glfwMakeContextCurrent()Black screenClear buffer + swap buffers7️⃣ (Optional) VS Code Task Configuration
You can automate build using tasks.json if you want.
✅ Summary
Install compiler + VS Code
Add GLFW + GLAD
Correct folder structure
Compile manually using g++
If you want, I can:

Configure tasks.json
Set up CMake
Explain Linux / macOS setup
Fix your existing OpenGL code
Just tell me 👍
