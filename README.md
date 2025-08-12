
# Guía de instalación ROS2 humble en ubunto


ROS2 (Robot Operating System 2) Humble Hawksbill es una distribución LTS (Long Term Support) de
ROS2 lanzada en mayo de 2022. Esta guía te llevará paso a paso para la
intalación en Ubuntu 22.04


# Preparación del sistema
## 1.-Actualizar el sistema

Antes de comenzar, es importante tener el sistema completamente actualizado:

```bash
 sudo apt update && sudo apt upgrade -y
```

## 2.- Verificar versión de ubunto.
La salida debe mostrar "22.04" en la línea de Release para poder continuar.
```bash 
lsb_release -a
```


## 3.- Instalar herramientas básicas

```bash 
sudo apt install software-properties-common curl wget gnupg lsb-release -y
```



# Instalación de ROS2 humble

## 1.-Configurar las Claves GPG
Las claves GPG aseguran que los paquetes descargados sean auténticos:
```bash 
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/sh
```

## 2.- Agregar el Repositorio de ROS2
Repositorio oficial de ROS2 en tu sistema:
```bash 
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-
```

## 3.- Actualizar paquetes

```bash 
sudo apt update
```

## 4.- Instalación de ROS2 humble 
ROS2 tiene distintas opciones de instalación en este caso nos enfocaremos en la versión completa: 

```bash 
sudo apt install ros-humble-desktop -y
```


# Configuración del entorno


## 1.- Configurar variables de entorno 
Para usar ROS2, necesitas cargar las variables de entorno en cada sesión de terminal:

```bash 
source /opt/ros/humble/setup.bash
```
## 2.- Configuración Automática

Para que ROS2 se cargue automáticamente en cada nueva terminal:
```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
```

## 3.- Recargar la Configuración
```bash 
source ~/.bashrc
```

## 4.- Verificar variables de entorno
Verifique que las variables estan correctamente Configuradas: 
Deberian salir variables como: ROS_VERSION = 2 & ROS_DISTRO = humble.
```bash 
printenv | grep ROS
```

# Herramientas Adicionales 

## 1.- Instalar Colcon  
Colcon es la herramienta de construccion estandar para ROS2
```bash 
sudo apt install python3-colcon-common-extensions -y
```

## 2.- Instalar Rosdep
Rosdep gestiona las dependencias de los paquetes de ROS
```bash 
sudo apt install python3-rosdep -y
```

Iniciar rosdep: 
```bash 
sudo rosdep init 
rosdep update
```


# Verificar la instalación 

## 1.- Verificar version 
```bash 
ros2 --version 
```
## 2.- Prueba basica de un nodo 
Nodo publicador

```bash 
ros2 run demo_nodes_cpp talker
```

Nodo suscriptor 
```bash 
ros2 run demo_nodes_py listener
```

Resultado: "Hello World: 1", "Hello World: 2", etc., en el talker,
y "I heard: [Hello World: 1]" en el listener.

# ¡Felicitaciones! Has instalado exitosamente ROS2 Humble en tu sistema Ubuntu


Esta guía ha sido creada para facilitar la instalación de ROS2 Humble. Para obtener la información más
actualizada, consulta siempre la documentación oficial de ROS2.









