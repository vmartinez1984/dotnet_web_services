# Convenciones en el código

En algunos casos su proyecto esta avanzado y no será viable hacer refactorizaciones por el tiempo. Pero al menos en los ejercicios de la clase deberan de contener al menos 3 clases con las convenciones que siguen o mínimo siempre respetar las suyas que este usando en su proyecto.

- Uso de UpperCamelCase

- Una clase y/o metodo una responsabilidad
```
/// <summary>
/// Esta clase se encarga de hacer operaciones SELECT, UPDATE e INSERT en la tabla de Pelicula
/// </summary>
public class PeliculaRepositorio
{
    /// <summary>
    /// Agregar Pelicula
    /// </summary>
    /// <param name="pelicula"></param>
    /// <param name="archivo"></param>
    /// <returns></returns>
    public async Task<int> AgregarAsync(PeliculaEntidad pelicula)
    {
        // Aqui la logica para insertar en la db
    }

    /// <summary>
    /// Obtine la pelicula por id o encodedkey
    /// </summary>
    /// <param name="peliculaId"></param>
    /// <returns></returns>
    public async Task<PeliculaEntidad> ObtenerPorIdAsync(string peliculaId)
    {
        //Aqui la logica para obtener un registro de la db por el Id
    }

    /// <summary>
    /// Paginada de las peliculas
    /// </summary>
    /// <param name="paginador"></param>
    /// <returns></returns>
    public async Task<List<PeliculaEntidad>> ObtenerAsync(Paginador paginador)
    {
        //Lógica para obtener una lista paginada de elementos de la db 
    }

    /// <summary>
    /// Actulizar registro de pelicula
    /// </summary>
    /// <param name="pelicula"></param>
    /// <returns></returns>
    public Task ActualizarAsync(PeliculaEntidad pelicula)
    {
        //Actualizar el elemento en la db
    }
}
```

- Todo el código será revisado en github, asi que hagalo publico o agregueme como colaborador. 
Mis datos en github:
    - vmartinez1984 
    - ahal_tocob@hotmail.com 

- Use nombres representativos y descriptivos, de uniformidad a su código. Por ejemplo cuando agregue un objeto, procure que su metodos se llamen igual, en el metodo siguiente puede pertenecer a Usuarios, Productos
```
public async Task<int> AgregarAsync(Entidad entidad)
{
    //Logica
}
```
- Use convenciones, postfijos y prefijos, 
    - por ejemplo todas las clases que esten relacionadas con la base de datos en el mapeo.
        - UsuarioEntidad
        - ProductoEntidad
    - Los dto que tengan el postfijo Dto
        - UsuarioDto
        - ProductoDto
    - En los prefijos, las interfaces
        - IUsuarioRepositorio
        - IProductoRepositorio

- Coloque comentarios en sus metodos, clases.

- Coloque un archivo readme, describiendo lo que hace su proyecto. Tambien es recomendable que anote las librerias con las versiones, algunos pasos para instalar, configurar etc.