# NavBot: Robot Diferencial Autónomo en ROS 2 Jazzy

![ROS 2](https://img.shields.io/badge/ROS_2-Jazzy-22314E?style=for-the-badge&logo=ros&logoColor=white)
![Gazebo](https://img.shields.io/badge/Gazebo-Harmonic-FF6F00?style=for-the-badge&logo=gazebo&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-24.04-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

Este repositorio contiene la implementación completa de un robot móvil de tracción diferencial simulado en **Gazebo Harmonic** y controlado mediante **ROS 2 Jazzy Jalisco**. El proyecto abarca desde el diseño URDF hasta la navegación autónoma con el stack **Nav2**.

## 📋 Tabla de Contenidos
- [Características](#-características)
- [Prerrequisitos](#-prerrequisitos)
- [Instalación](#-instalación)
- [Uso](#-uso)
  - [1. Simulación y Teleoperación](#1-simulación-y-teleoperación)
  - [2. Mapeo (SLAM)](#2-mapeo-slam)
  - [3. Navegación Autónoma (Nav2)](#3-navegación-autónoma-nav2)
- [Arquitectura del Robot](#-arquitectura-del-robot)
- [Solución de Problemas Comunes](#-solución-de-problemas-comunes)
- [Autor](#-autor)

## 🚀 Características
* **Simulación Física:** Modelo URDF/Xacro con propiedades inerciales y de colisión realistas.
* **Sensores:** Lidar 2D (GPU Ray Sensor) simulado para percepción de obstáculos.
* **Control:** Plugin `DiffDrive` de Gazebo para odometría y control de velocidad.
* **Mapeo:** Generación de mapas de ocupación mediante `slam_toolbox` (Async).
* **Navegación:** Planificación de trayectorias y evasión de obstáculos con **Nav2**.

## 🛠 Prerrequisitos
* **Sistema Operativo:** Ubuntu 24.04 LTS (Nativo recomendado).
* **ROS 2:** Jazzy Jalisco.
* **Simulador:** Gazebo Harmonic.
* **Dependencias de Python:**
    ```bash
    sudo apt install ros-jazzy-navigation2 ros-jazzy-nav2-bringup ros-jazzy-slam-toolbox ros-jazzy-xacro ros-jazzy-robot-localization
    ```

## 📦 Instalación

1.  **Clonar el repositorio:**
    ```bash
    mkdir -p ~/ros2_ws/src
    cd ~/ros2_ws/src
    git clone [https://github.com/TU_USUARIO/nav_bot.git](https://github.com/TU_USUARIO/nav_bot.git)
    ```

2.  **Construir el paquete:**
    ```bash
    cd ~/ros2_ws
    colcon build --symlink-install
    source install/setup.bash
    ```

## 🎮 Uso

### 1. Simulación y Teleoperación
Lanza el robot en Gazebo y habilita el control manual.
```bash
# Terminal 1: Simulación
ros2 launch nav_bot sim.launch.py

# Terminal 2: Teleoperación
ros2 run teleop_twist_keyboard teleop_twist_keyboard
