        By Dazhai.exe

    1-Añadir un estudiante. . . 
    2-Listado de estudiantes. . .
    3-Modificar datos de un estudiante. . .
    4-Eliminar un estudiante (RIAAAN QUEMA'O)
    5-Exportar a un HTML. . .
    6-Acerca de YOlanda osea mi. . .
    x- Salir
====================================================================================== 
    ");

    var opcion = Utils.atiendemeetestring("Ingrese una opcion:");

    switch (opcion.ToLower())
    {
        case "1":
            Console.Clear();
            Console.WriteLine("Ingrese el nombre del estudiante:");
            Utils.reproducemeEseAudioAlfavor("anadir.wav");
            var e = new Estudiantes();
            e.Matricula = Utils.atiendemeetestring("Ingrese la Matricula:");
            e.Nombre = Utils.atiendemeetestring("Ingrese el Nombre:");
            e.Apellido = Utils.atiendemeetestring("Ingrese el Apellido:");
            e.Edad = Utils.atiendemeetestring("Ingrese la edad:");
            e.N1 = Utils.atiendemeEtedouble("Ingrese la Nota 1:");
            e.N2 = Utils.atiendemeEtedouble("Ingrese la Nota 2:");
            estudiantes.Add(e);
            Utils.MensajeAlert("Estudiante agregado :D", ConsoleColor.Cyan);
            break;

        case "2":
            Console.Clear();
            Console.WriteLine("Listado de Estudiantes");
            foreach (var Estudiantes in estudiantes)
            {
                Console.WriteLine(@$"
===============================================================================                
                Matricula: {Estudiantes.Matricula}
                Nombre: {Estudiantes.Nombre}
                Apellido: {Estudiantes.Apellido}
                Edad: {Estudiantes.Edad}
                Nota 1: {Estudiantes.N1}
                Nota 2: {Estudiantes.N2}
                Promedio: {Estudiantes.promedio()}
                Literal: {Estudiantes.literal()}
===============================================================================
                ");
                Utils.reproducemeEseAudioAlfavor("listado.wav");
            }
            Utils.unvoidcasual("Presiona cualquier tecla para continuar. . .");
            break;

        case "3":
            estudiantes = Procesos.Modificar(estudiantes);
            break;
        case "4":
            estudiantes = Procesos.Eliminar(estudiantes);
            break;

        case "5":
            Procesos.Exportar(estudiantes);
            break;

        case "6":
            Procesos.acercademi();
            break;

        case "x":
            continuar = false;
            Utils.BabayCuidateYADioKtemecuide("Gracias por su tiempo, vuelva pronto :D");
            Utils.reproducemeEseAudioAlfavor("adio.wav");

            var tmp = Newtonsoft.Json.JsonConvert.SerializeObject(estudiantes);
            System.IO.File.WriteAllText("datos.Json", tmp);

            break;
        default:
            Utils.ErrorAlert("Papi yo hablo ruso?, que elige una de las opciones en pantalla");
            break;
