# RegistryDIE

Este repositorio es un registro de paquetes de Julia para su utilización en el Departamento de Investigaciones Económicas. Este registro permite agregar paquetes a nuestros proyectos en Julia y llevar un control de las versiones de los paquetes registrados en él. Este control de versiones es útil si necesitamos la funcionalidad de un paquete en una versión específica. 

## Agregar el registro a la instalación de Julia
Para agregar este registro a tu instalación de Julia, simplemente ejectua en el REPL de Julia: 

```julia-repl
julia> ]
(@v1.6) pkg> registry add https://github.com/DIE-BG/RegistryDIE
     Cloning registry from "https://github.com/DIE-BG/RegistryDIE"
     (...)
```

Una vez agregado este registro privado, el repositorio estará disponible en el directorio `C:\Users\<USER>\.julia\registries\RegistryDIE`, donde `<USER>` es el usuario de nuestro equipo. 

## Agregar un paquete del registro a un proyecto

Supongamos que vamos a trabajar un proyecto con los datos del IPC de Guatemala. Actualmente existe un paquete que nos provee esos datos, denominado `CPIDataBase.jl`, el cual se encuentra en la organización DIE-BG. 

Por ejemplo, para instalar este paquete en el entorno global después de instalar el registro, simplemente ejecutamos: 

```julia-repl
julia> ]
(@v1.6) pkg> add CPIDataBase
    Updating registry at `C:\Users\RRCP\.julia\registries\General`
    Updating git-repo `https://github.com/JuliaRegistries/General.git`
    Updating registry at `C:\Users\RRCP\.julia\registries\RegistryDIE`
    Updating git-repo `https://github.com/DIE-BG/RegistryDIE`
    Resolving package versions...
    Updating `C:\Users\RRCP\AppData\Local\Temp\jl_1ZmwyT\Project.toml`
  [bc2aee9a] + CPIDataBase v0.3.6
    Updating `C:\Users\RRCP\AppData\Local\Temp\jl_1ZmwyT\Manifest.toml`
  [bc2aee9a] + CPIDataBase v0.3.6
    (...)
```

Note que el registro privado se actualizará cada vez que deseemos modificar el entorno de trabajo.

Posteriormente, para utilizar el paquete simplemente hacemos: 

```julia-repl
julia> using CPIDataBase
[ Info: Cargando datos de Guatemala...
(...)
```

## Agregar un paquete a este registro

Para agregar más paquetes a este registro, debemos seguir las instrucciones detalladas en la documentación del paquete [LocalRegistry.jl](https://github.com/GunnarFarneback/LocalRegistry.jl#register-a-package). 

Debido a las restricciones de red del Banco, es posible que la función `register(package)` detallada en la documentación no actualice correctamente el repositorio remoto del registro. En este caso, la solución consiste en los siguientes pasos: 

1. Agregar el repositorio local del registro a Github Desktop. Esto se hace en la opción `File -> Add local repository`, seleccionando la ruta hacia el registro en el directorio `C:\Users\<USER>\.julia\registries\RegistryDIE`.
2. Al utilizar la función de registro, llamarla con el argumento `push=false`. Por ejemplo: `register(package, push=false)`. 
3. Regresar a Github Desktop para enviar los cambios al repositorio remoto. Para esto hacemos `Push` en la aplicación. 

## Consultas

Cualquier otra consulta realizarla con [Rodrigo Chang](mailto:rrcp@banguat.gob.gt).