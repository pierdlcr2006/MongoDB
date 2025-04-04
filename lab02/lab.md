# Lab 02 - Base de Datos Avazandas - Mongo

## 1. Colección Áreas

- ### Creación de colección Áreas
```javascript

    db.createCollection('Areas');
    show collections;

```
- ### Adición de documentos a la colección Áreas

```javascript

    db.Areas.insertOne({Nombre : 'Docencia',Abreviatura : 'Doc',Estado : 'A'});
    db.Areas.find({},{_id:0});

    db.Areas.insertOne({Nombre : 'Informatica',Abreviatura : 'Infor', Estado : 'A'})
    db.Areas.find({Nombre : 'Informatica'},{_id :0})

    db.Areas.find({Nombre:{$in:['Electronica','Mecanica','Estudios Generales']}},{_id : 0});

    db.Areas.insertMany([{Nombre : 'Electronica',Abreviatura : 'Elect', Estado : 'A'},
    {Nombre : 'Mecanica',Abreviatura : 'Mec', Estado : 'A'},
    {Nombre : 'Estudios Generales',Abreviatura : 'EEGG', Estado : 'A'}
    ])
    //-Muestra todos los documentos menos el ID
    db.Areas.find({},{_id:0})
    db.Areas.find({Nombre : {$in : ['Electronica','Informatica','Estudios Generales']}},
    {_id : 0});

```

- ### Modificación de documentos de la colección Áreas

```javascript

    db.Areas.insertMany([{Nombre : 'Administracion',Abreviatura : 'Adm', Estado : 'A'},{Nombre : 'Tecnologias de Informacion y Seguridad',Abreviatura : 'TIS', Estado : 'A'},{Nombre : 'Seguridad',Abreviatura : 'Seg', Estado : 'A'}])

    db.Areas.find({Nombre : {$in : ['Administracion','Tecnologias de Informacion y Seguridad','Seguridad']}},{_id : 0});

    db.Areas.insertMany([
    {Nombre : 'Area1',Abreviatura : 'A1', Estado : 'X'},
    {Nombre : 'Area2',Abreviatura : 'A2', Estado : 'X'},
    {Nombre : 'Area3',Abreviatura : 'A3', Estado : 'X'}
    ])

    //-Actualizar
    db.Areas.updateOne(
    {Nombre : 'Area1'},
    {$set: {Nombre: 'Area No 1',Abreviatura : 'Ar1', Estado : 'N'}
    })
    db.Areas.find({Nombre : 'Area No 1'},{_id : 0})

    db.Areas.updateOne(
    {Nombre : 'Area2'},
    {$set : {Nombre : 'Area No 2',Abreviatura : 'Ar2', Estado:'P'}}
    )
    db.Areas.find({Nombre : 'Area No 2'},{_id : 0})

    db.Areas.updateOne(
    {Nombre : 'Area No3'},
    {$set : {Nombre : 'Area No 3'}}
    )
    db.Areas.find({Nombre : 'Area No 3'},{_id : 0})

    db.Areas.updateOne({Nombre : 'Area No 1'},{$set:{Estado : 'A'}})
    db.Areas.find({Nombre : 'Area No 1'},{_id : 0})

    db.Areas.updateOne({Nombre : 'Area No 2'},{$set:{Abreviatura : 'ARE2',Estado : 'A'}})
    db.Areas.find({Nombre:'Area No 2'},{_id:0})

    db.Areas.updateOne({Nombre : 'Area No 3'},{$set:{Abreviatura : 'AN3'}})
    db.Areas.find({Nombre : 'Area No 3'},{_id : 0})

```
- ### Elimiación de documentos

```javascript

    // Eliminar
    db.Areas.deleteOne({Nombre : 'Area No 1'})
    db.Areas.find({Nombre : 'Area No 1'})

    db.Areas.deleteOne({Nombre : 'Area No 2'})
    db.Areas.find({Nombre:'Area No 2'})

    db.Areas.deleteOne({Abreviatura : 'AN3'})
    db.Areas.find({Abreviatura : 'AN3'})

```
- ### Consulta de documentos

```JavaScript

    db.Areas.find({},{_id : 0})

    //-Mostrar solo ciertos campos de cada documento
    db.Areas.find({},{_id : 0,Abreviatura : 0})
    db.Areas.find({},{_id : 0,Estado : 1,Nombre : 1})

    db.Areas.find({},{_id : 0,Nombre : 0})

    db.Areas.find({Nombre:'Electronica'})

    db.Areas.find({Nombre : 'Electronica'},{_id : 0,Abreviatura:0})

    //-$or
    db.Areas.find({$or:[{Nombre:'Electronica'},{Nombre:'Informatica'}]},{_id:0 , Abreviatura : 0})

    //-$in
    db.Areas.find({Nombre : {$in : ['Electronica','Informatica'] } } , {_id : 0,Abreviatura : 0})

    //-findOne muestra el primer docuemento que cumpla la condición

    db.Areas.findOne({Estado : 'A'},{_id : 0,Abreviatura : 0})

    //-.sort en orden ascendente +1 por campo Nombre
    db.Areas.find({},{_id:0,Abreviatura :0}).sort({Nombre : 1})

    //-.sort en orden descendente - 1 por campo Nombre
    db.Areas.find({},{_id:0,Abreviatura:0}).sort({Nombre : -1})

    //-.limit
    db.Areas.find({},{_id:0,Abreviatura:0}).limit(3)

```

## 2. Colección Cargos y Mascotas

```JavaScript

    db.Mascotas.insertMany([
    {_id: 1, nombre: 'Boby', tipo: 'Perro', genero: 'M', fecha_nacimiento: new Date('2013-01-23')},
    {_id: 2, nombre: 'Keyla', tipo: 'Gato', genero: 'H', fecha_nacimiento: new Date('2015-09-12')},
    {_id: 3, nombre: 'Lasie', tipo: 'Perro', genero: 'H', fecha_nacimiento: new Date('2012-08-31')},
    {_id: 4, nombre: 'Feli', tipo: 'Gato', genero: 'M', fecha_nacimiento: new Date('2011-10-15')},
    {_id: 5, nombre: 'Lucas', tipo: 'Perro', genero: 'M', fecha_nacimiento: new Date('2014-04-13')},
    {_id: 6, nombre: 'Messi', tipo: 'Gato', genero: 'M', fecha_nacimiento: new Date('2015-09-12')},
    {_id: 7, nombre: 'Nana', tipo: 'Perro', genero: 'H', fecha_nacimiento: new Date('2015-02-18')},
    {_id: 8, nombre: 'Pepa', tipo: 'Loro', genero: 'H', fecha_nacimiento: new Date('2015-11-27')}
    ]);

    db.Cargos.insertMany([
    {_id: 1,nombre: 'Administrador', sueldo: 9000},
    {_id: 2,nombre: 'Contador', sueldo: 8500},
    {_id: 3,nombre: 'Gerente', sueldo: 13000},
    {_id: 4,nombre: 'Supervisor', sueldo: 11000},
    {_id: 5,nombre: 'Ingeniero', sueldo: 10500},
    {_id: 6,nombre: 'Tecnico', sueldo: 5000},
    {_id: 7,nombre: 'Secretaria', sueldo: 4000},
    {_id: 8,nombre: 'Practicante', sueldo: 1200},
    {_id: 9,nombre: 'Capataz', sueldo: 3500}
    ]);

    db.Areas.find()
    db.Mascotas.find({})
    db.Cargos.find({})

    db.Mascotas.find({},{_id : 0,fecha_nacimiento:0})
    db.Mascotas.find({tipo : 'Perro'},{_id:0,fecha_nacimiento:0})
    db.Mascotas.find({tipo : 'Perro',genero:'M'},{_id:0,fecha_nacimiento:0})
    db.Mascotas.insertOne( { _id: 9, nombre:'Mirna', tipo:'Gato', genero:'H' } );

    db.Cargos.insertOne({_id:10,nombre:'De la Cruz'})
    db.Mascotas.insertOne(
    { _id:10, nombre:'Kaco', tipo:'Perro', genero:'M',fecha_nacimiento: "09/23/2015", origen: "Selva peruana" }
    );

    db.Cargos.insertOne({_id:11,nombre:'Piero',sueldo:'5000',comision : '1000',estado : 'A'})

```
## 3. Tarea 2

```JavaScript

    //Busca todo donde tipo no sea igual a gato {$not{$eq:'Gato'}}
    db.Mascotas.find( { tipo: { $not: { $eq: "Gato"} } }, {_id:0, fecha_nacimiento:0 } );

    //Busca todo donde sueldo se mayor que 6500 {sueldo:{$gt:6500}}
    db.Cargos.find( { sueldo: { $gt: 6500 } }, { _id:0, nombre:1, sueldo:1 } );

    //Busca todo donde el tipo no sea ni gato y el genero no sea M
    db.Mascotas.find( { $nor: [ { tipo: "Gato" }, { genero: 'M' } ] },{ _id:0, nombre:1, tipo:1, genero:1 } );

    //Busca todo si el campo origen existe
    db.Mascotas.find( { origen: { $exists: true } } );

    //Busca todo los documentos en donde el campo origen no exista
    db.Mascotas.find( { origen: { $not: { $exists: true } } } );

    //Busca todo los documentos en donde exista el campo sueldo y cuyo monto sea mayor a 5000 gt=greather than
    db.Cargos.find({sueldo:{$exists:true,$gt:5000}})

    //Busca todo los documentos en donde exista el campo sueldo y cuyo monto sea menor a 5000 lt=less than
    db.Cargos.find({sueldo:{$exists:true,$lt:5000}})

    //sueldo exista y este en un rango de
    db.Cargos.find({sueldo:{$exists:true,$gt:5000,$lt:10000}})


    //Busca todo los docuemntso cuyos nombres inician con la letra L $regex/^/
    db.Mascotas.find({nombre:{$regex:/^L/}})

    //Busca todo los docuemntos cuyos nombres contengan la letra L en cualquier posicion sin importar mayus ni minus $regex/L/i
    db.Mascotas.find({nombre:{$regex:/L/i}})

    //Busca todo los docuemntos cuyos nombres inician con la letra L y ademas tenga la letra a en cualquier posicion
    db.Mascotas.find({$and:[{nombre:{$regex:/^L/}},{nombre:{$regex:/a/}}]})

    //Busca todo los documentos cuyos nombres no inicien con la letra L, mostrar solo nombre
    db.Mascotas.find({nombre:{$not:{$regex:/^L/}}},{_id:0,nombre:1})

    //Busca todo los documentos cuyos nombres terminen en la letra a, mostrar solo nombre
    db.Mascotas.find({nombre:{$regex:/a$/}},{_id:0 ,nombre:1})

    //Busca todo los documentos cuyos nombres no ternminen en la letra a, mostrar solo nombre
    db.Mascotas.find({nombre:{$not:{$regex:/a$/}}},{_id:0,nombre:1})

    //Busca todo los documentos cuyos nombres empiezan por L o B o M, mostrar solo nombre
    db.Mascotas.find({$or:[{nombre:{$regex:/^L/}},{nombre:{$regex:/^B/}},
    {nombre:{$regex:/^M/}}]},{_id:0,nombre:1})
    //Forma mas rápida ⬇️
    db.Mascotas.find({nombre:{$regex:'[L,B,M]'}},{_id:0,nombre:1})

    //Busca todo los documentos cuyos nombres no empiecen por L o B o M, mostrar solo nombre
    db.Mascotas.find({nombre:{$not:{$regex:'[L,B,M]'}}},{_id:0,nombre:1})
    //Forma mas rápida ⬇️
    db.Mascotas.find({nombre:{$not:/[L,B,M]/}},{_id:0,nombre:1})

```