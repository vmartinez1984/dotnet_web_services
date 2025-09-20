# CRUD de peliculas

Este es un ejemplo básico para generar un CRUD

# PeliculaEntidad

Una entidad es un clase con propiedades que se mapea contra la base de datos.
```
public class PeliculaEntidad
{
    public int Id { get; set; }

    [Required]
    [MaxLength(50)]
    public string Titulo { get; set; }

    [MaxLength(250)]
    public string Sinopsis { get; set; }

    public bool Vista { get; set; } = false;
    
    public DateTime FechaDeRegistro { get; set; } = DateTime.Now;
}
```
# Instalar los nugets

dotnet add package Microsoft.EntityFrameworkCore
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools

# Generar la clase dbcontext
```
 public class AppDbContext : DbContext
 {
     private readonly string _connectionString;

     public DbSet<PeliculaEntidad>   Pelicula { get; set; }

     public AppDbContext(IConfiguration configuration)
     {
         _connectionString = configuration.GetConnectionString("PeliculaDB");
     }

     protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
     {
         optionsBuilder.UseSqlServer(_connectionString);
        base.OnConfiguring(optionsBuilder);
     }
 }
```

# Configurar el appsettins 
```
"ConnectionStrings": {
    "PeliculaDB": "Server=localhost;Database=test;User Id=sa;Password=Macross#2012; TrustServerCertificate=True;"
  }
```

# verificar si esta isntalado el EF
```
dotnet ef --version
```
Instalar en caso de no tenerlo instalado
```
dotnet tool install --global dotnet-ef
```

# Hacer la migracion
```
dotnet ef migrations add Inicial
```
# Aplicar migración
```
dotnet ef database update
```

# ¿Que es un Dto?

Data Transfer Object, es un objeto que contiene unicamente propiedades y se utiliza de cara al usuario, para ocultar algunas propiedades o simplemente para mostar las propiedades que se ocupan.

## PeliculaDtoIn
Clase de entrada, propiedades con decoradores DataAnnotations y validaciones, estra clase dtoIn se mapea con la clase entidad.

DtoIn -> Entidad
```
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;

public class PeliculaDtoIn
{
    [MaxLength(64)]
    public string Encodedkey { get; set; } = Guid.NewGuid().ToString();

    [Required]
    [MaxLength(64)]
    public string Titulo { get; set; }

    [Required]
    [MaxLength(1024)]
    public string Sinopsis { get; set; }

    public IFormFile PosterFormFile { get; set; }

    [MaxLength(1024)]
    public string Trailer { get; set; }
}
```

## PeliculaDto

La clase dto se mapea con la clase entidad, la cual viene de la base de datos.

Entidad -> Dto
```
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;
public class PeliculaDto
{
    public int Id { get; set; }

    public string Encodedkey { get; set; }

    [DisplayName("Título")]
    public string Titulo { get; set; }

    public string Sinopsis { get; set; }

    public string Trailer { get; set; }

    public bool Vista { get; set; }

    [DisplayName("Fecha de registro")]
    public DateTime FechaDeRegistro { get; set; }

}
```

## PeliculaDtoUpd
Esta clase se usa para la operaciópn de actualización.
- Se busca la entidad con el Id que viene en la Url
- La entidad se actuliza con los datos del DtoUpd
```
public class PeliculaDtoUpd
{
    [Required]
    [MaxLength(64)]
    public string Titulo { get; set; }

    [Required]
    [MaxLength(1024)]
    public string Sinopsis { get; set; }

    public IFormFile PosterFormFile { get; set; }

    [MaxLength(1024)]
    public string Trailer { get; set; }
}
```