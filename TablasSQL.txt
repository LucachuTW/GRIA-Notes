Ejercicio 1:

CREATE TABLE Becarios (
    DNI VARCHAR(10) PRIMARY KEY,
    NumeroSeguridadSocial VARCHAR(15),
    Nombre VARCHAR(50),
    Apellidos VARCHAR(50),
    FechaNacimiento DATE,
    Edad INT
);

CREATE TABLE Laboratorios (
    CodigoIdentificacion INT PRIMARY KEY,
    NumeroPlanta INT,
    SupervisorDNI VARCHAR(10),
    FOREIGN KEY (SupervisorDNI) REFERENCES Becarios(DNI)
);

CREATE TABLE Ordenadores (
    DireccionIP VARCHAR(15) PRIMARY KEY,
    FechaCompra DATE,
    LaboratorioCodigo INT,
    FOREIGN KEY (LaboratorioCodigo) REFERENCES Laboratorios(CodigoIdentificacion)
);

CREATE TABLE Componentes (
    CodigoModelo INT PRIMARY KEY,
    Descripcion VARCHAR(100),
    FabricanteCodigo INT,
    FOREIGN KEY (FabricanteCodigo) REFERENCES Fabricantes(Codigo)
);

CREATE TABLE Fabricantes (
    Codigo INT PRIMARY KEY,
    Nombre VARCHAR(100),
    Telefono1 VARCHAR(15),
    Telefono2 VARCHAR(15),
    DireccionWeb VARCHAR(100)
);

ALTER TABLE Laboratorios
ADD CONSTRAINT FK_Laboratorios_SupervisorDNI
FOREIGN KEY (SupervisorDNI) REFERENCES Becarios(DNI);
ALTER TABLE Becarios
ADD SuplenteDNI VARCHAR(10),
ADD CONSTRAINT FK_Becarios_SuplenteDNI
FOREIGN KEY (SuplenteDNI) REFERENCES Becarios(DNI);

CREATE TABLE OrdenadoresComponentes (
    DireccionIPOrdenador VARCHAR(15),
    CodigoModeloComponente INT,
    PRIMARY KEY (DireccionIPOrdenador, CodigoModeloComponente),
    FOREIGN KEY (DireccionIPOrdenador) REFERENCES Ordenadores(DireccionIP),
    FOREIGN KEY (CodigoModeloComponente) REFERENCES Componentes(CodigoModelo)
);

Ejercicio 2:

CREATE TABLE Clientes (
    CodigoCliente INT PRIMARY KEY,
    DNI VARCHAR(10) UNIQUE,
    Nombre VARCHAR(50),
    Direccion VARCHAR(100),
    Telefono VARCHAR(15),
    AvalCodigoCliente INT,
    FOREIGN KEY (AvalCodigoCliente) REFERENCES Clientes(CodigoCliente)
);

CREATE TABLE Reservas (
    CodigoReserva INT PRIMARY KEY,
    CodigoCliente INT,
    FechaInicio DATE,
    FechaFinal DATE,
    PrecioTotal DECIMAL(10,2),
    CochesEntregados BOOLEAN,
    FOREIGN KEY (CodigoCliente) REFERENCES Clientes(CodigoCliente)
);

CREATE TABLE Coches (
    Matricula VARCHAR(10) PRIMARY KEY,
    Modelo VARCHAR(50),
    Color VARCHAR(20),
    Marca VARCHAR(30),
    GarajeCodigo INT,
    FOREIGN KEY (GarajeCodigo) REFERENCES Garajes(CodigoGaraje)
);

CREATE TABLE DetallesReserva (
    CodigoReserva INT,
    MatriculaCoche VARCHAR(10),
    PrecioAlquiler DECIMAL(10,2),
    LitrosGasolina DECIMAL(5,2),
    PRIMARY KEY (CodigoReserva, MatriculaCoche),
    FOREIGN KEY (CodigoReserva) REFERENCES Reservas(CodigoReserva),
    FOREIGN KEY (MatriculaCoche) REFERENCES Coches(Matricula)
);

CREATE TABLE Garajes (
    CodigoGaraje INT PRIMARY KEY,
    Direccion VARCHAR(100),
    NumeroPlazas INT
);

CREATE TABLE Agencias (
    CodigoAgencia INT PRIMARY KEY,
    Direccion VARCHAR(100),
    Localidad VARCHAR(50)
);

Ejercicio 3:

CREATE TABLE Aplicaciones (
    IDAplicacion INT PRIMARY KEY,
    Nombre VARCHAR(100),
    Descripcion TEXT
);

CREATE TABLE Versiones (
    IDVersion INT PRIMARY KEY,
    IDAplicacion INT,
    NumeroVersion INT,
    FOREIGN KEY (IDAplicacion) REFERENCES Aplicaciones(IDAplicacion)
);

CREATE TABLE Incidencias (
    IDIncidencia INT PRIMARY KEY,
    IDVersion INT,
    ProgramadorAbreDNI VARCHAR(10),
    ProgramadorAtiendeDNI VARCHAR(10),
    TiempoAbierta INT, -- En minutos o horas, dependiendo de la unidad de tiempo que se prefiera
    FechaApertura DATETIME,
    FechaCierre DATETIME,
    FOREIGN KEY (IDVersion) REFERENCES Versiones(IDVersion),
    FOREIGN KEY (ProgramadorAbreDNI) REFERENCES Programadores(DNI),
    FOREIGN KEY (ProgramadorAtiendeDNI) REFERENCES Programadores(DNI)
);

CREATE TABLE Programadores (
    DNI VARCHAR(10) PRIMARY KEY,
    NumeroSeguridadSocial VARCHAR(15),
    Nombre VARCHAR(50),
    CorreoElectronico VARCHAR(100)
);

Ejercicio 4:

CREATE TABLE Departamentos (
    CodigoDepartamento INT PRIMARY KEY,
    NombreDepartamento VARCHAR(100),
    DirectorNRP VARCHAR(10),
    FOREIGN KEY (DirectorNRP) REFERENCES Profesores(NRP)
);

CREATE TABLE Profesores (
    NRP VARCHAR(10) PRIMARY KEY,
    NombreProfesor VARCHAR(100),
    AreaConocimiento VARCHAR(100),
    Categoria VARCHAR(50),
    CodigoDepartamento INT,
    FOREIGN KEY (CodigoDepartamento) REFERENCES Departamentos(CodigoDepartamento)
);

CREATE TABLE Asignaturas (
    CodigoAsignatura INT PRIMARY KEY,
    NombreAsignatura VARCHAR(100),
    Creditos INT,
    Caracter VARCHAR(20),
    Curso INT
);

CREATE TABLE Grupos (
    IDGrupo INT PRIMARY KEY,
    NumeroGrupo INT,
    MaxAlumnos INT,
    TipoGrupo VARCHAR(20),
    CodigoAsignatura INT,
    FOREIGN KEY (CodigoAsignatura) REFERENCES Asignaturas(CodigoAsignatura)
);

CREATE TABLE Alumnos (
    DNI VARCHAR(10) PRIMARY KEY,
    NombreAlumno VARCHAR(100),
    FechaNacimiento DATE,
    Direccion VARCHAR(100),
    Beca VARCHAR(50)
);

CREATE TABLE Matriculas (
    DNIAlumno VARCHAR(10),
    IDGrupo INT,
    Convocatoria INT,
    Calificacion FLOAT,
    PRIMARY KEY (DNIAlumno, IDGrupo, Convocatoria),
    FOREIGN KEY (DNIAlumno) REFERENCES Alumnos(DNI),
    FOREIGN KEY (IDGrupo) REFERENCES Grupos(IDGrupo)
);

Ejercicio 5:

CREATE TABLE Hoteles (
    CodigoHotel INT PRIMARY KEY,
    NombreHotel VARCHAR(100),
    Direccion VARCHAR(100),
    Ciudad VARCHAR(50),
    Telefono VARCHAR(15),
    PlazasDisponibles INT
);

CREATE TABLE Vuelos (
    NumeroVuelo INT PRIMARY KEY,
    Fecha DATE,
    Hora TIME,
    Origen VARCHAR(50),
    Destino VARCHAR(50),
    PlazasTotales INT,
    PlazasTurista INT
);

CREATE TABLE Clientes (
    CodigoCliente INT PRIMARY KEY,
    Nombre VARCHAR(50),
    Apellidos VARCHAR(50),
    Direccion VARCHAR(100),
    Telefono VARCHAR(15)
);

CREATE TABLE Agencias (
    CodigoAgencia INT PRIMARY KEY,
    Direccion VARCHAR(100),
    Telefono VARCHAR(15)
);

CREATE TABLE ReservasVuelos (
    CodigoCliente INT,
    NumeroVuelo INT,
    Clase VARCHAR(20),
    PRIMARY KEY (CodigoCliente, NumeroVuelo),
    FOREIGN KEY (CodigoCliente) REFERENCES Clientes(CodigoCliente),
    FOREIGN KEY (NumeroVuelo) REFERENCES Vuelos(NumeroVuelo)
);

CREATE TABLE ReservasHoteles (
    CodigoCliente INT,
    CodigoHotel INT,
    Regimen VARCHAR(50),
    FechaLlegada DATE,
    FechaPartida DATE,
    PRIMARY KEY (CodigoCliente, CodigoHotel),
    FOREIGN KEY (CodigoCliente) REFERENCES Clientes(CodigoCliente),
    FOREIGN KEY (CodigoHotel) REFERENCES Hoteles(CodigoHotel)
);

CREATE TABLE AtencionClientes (
    CodigoCliente INT,
    CodigoAgencia INT,
    PRIMARY KEY (CodigoCliente, CodigoAgencia),
    FOREIGN KEY (CodigoCliente) REFERENCES Clientes(CodigoCliente),
    FOREIGN KEY (CodigoAgencia) REFERENCES Agencias(CodigoAgencia)
);


Ejercicio 6

CREATE TABLE Emisoras (
    CodigoEmisora VARCHAR(20) PRIMARY KEY,
    Ubicacion VARCHAR(100),
    FormatoEmision VARCHAR(20)
);

CREATE TABLE Programas (
    NombrePrograma VARCHAR(100) PRIMARY KEY,
    Tematica VARCHAR(100),
    FranjaHoraria VARCHAR(20),
    CodigoEmisora VARCHAR(20),
    PresentadorDNI VARCHAR(10),
    FOREIGN KEY (CodigoEmisora) REFERENCES Emisoras(CodigoEmisora),
    FOREIGN KEY (PresentadorDNI) REFERENCES Presentadores(DNI)
);

CREATE TABLE Ediciones (
    NumeroEdicion INT PRIMARY KEY,
    FechaEdicion DATE,
    HoraInicio TIME,
    HoraFin TIME,
    Duracion INT, -- En minutos o horas, dependiendo de la unidad de tiempo que se prefiera
    NumeroOyentes INT,
    ProgramaNombre VARCHAR(100),
    FOREIGN KEY (ProgramaNombre) REFERENCES Programas(NombrePrograma)
);

CREATE TABLE Presentadores (
    DNI VARCHAR(10) PRIMARY KEY,
    Nombre VARCHAR(50),
    Email VARCHAR(100),
    Telefono1 VARCHAR(15),
    Telefono2 VARCHAR(15),
    EsDirector BOOLEAN
);

CREATE TABLE Coordinaciones (
    CoordinadorDNI VARCHAR(10),
    ProgramaNombre VARCHAR(100),
    PRIMARY KEY (CoordinadorDNI, ProgramaNombre),
    FOREIGN KEY (CoordinadorDNI) REFERENCES Presentadores(DNI),
    FOREIGN KEY (ProgramaNombre) REFERENCES Programas(NombrePrograma)
);


Ejercicio 7:

CREATE TABLE Departamentos (
    NumeroDepartamento INT PRIMARY KEY,
    NombreDepartamento VARCHAR(100),
    EmpleadoDirectorSS VARCHAR(15),
    FechaInicioDireccion DATE,
    FOREIGN KEY (EmpleadoDirectorSS) REFERENCES Empleados(NumeroSS)
);

CREATE TABLE Proyectos (
    NumeroProyecto INT PRIMARY KEY,
    NombreProyecto VARCHAR(100),
    Lugar VARCHAR(100),
    NumeroDepartamento INT,
    FOREIGN KEY (NumeroDepartamento) REFERENCES Departamentos(NumeroDepartamento)
);

CREATE TABLE Empleados (
    NumeroSS VARCHAR(15) PRIMARY KEY,
    Nombre VARCHAR(50),
    Direccion VARCHAR(100),
    Salario DECIMAL(10, 2),
    Sexo CHAR(1),
    FechaNacimiento DATE,
    NumeroDepartamento INT,
    SupervisorNumeroSS VARCHAR(15),
    FOREIGN KEY (NumeroDepartamento) REFERENCES Departamentos(NumeroDepartamento),
    FOREIGN KEY (SupervisorNumeroSS) REFERENCES Empleados(NumeroSS)
);

CREATE TABLE TrabajaEn (
    EmpleadoNumeroSS VARCHAR(15),
    ProyectoNumero INT,
    HorasSemanales INT,
    PRIMARY KEY (EmpleadoNumeroSS, ProyectoNumero),
    FOREIGN KEY (EmpleadoNumeroSS) REFERENCES Empleados(NumeroSS),
    FOREIGN KEY (ProyectoNumero) REFERENCES Proyectos(NumeroProyecto)
);

CREATE TABLE Familiares (
    NSSFamiliar VARCHAR(15),
    Nombre VARCHAR(50),
    Sexo CHAR(1),
    FechaNacimiento DATE,
    Parentesco VARCHAR(50),
    EmpleadoNumeroSS VARCHAR(15),
    PRIMARY KEY (NSSFamiliar),
    FOREIGN KEY (EmpleadoNumeroSS) REFERENCES Empleados(NumeroSS)
);

