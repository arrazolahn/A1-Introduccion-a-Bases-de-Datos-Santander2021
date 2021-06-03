[`Introducción a Bases de Datos`](../../README.md) > [`Sesión 07`](../Readme.md) > `Reto 1`
	
## Reto 1: Agrupamientos

<div style="text-align: justify;">

### 1. Objetivos :dart: 

- Poner en práctica el uso de agrupamientos.

### 2. Requisitos :clipboard:

1. MongoDB Compass instalado.

### 3. Desarrollo :rocket:

Con base en el ejemplo 1, modifica el agrupamiento para que muestre el costo promedio por habitación por país de las propiedades de tipo casa.

```json

	[{$match: {
  property_type: "House",
  bedrooms: {$gte: 1}
}
}, {$addFields: {
   costo_recamara: {$divide: ["$price", "$bedrooms"]}
}}, {$group: {
  _id: "$address.country",
  recamaras: {
     $sum: 1
  },
  total: {
     $sum: "$costo_recamara"
  }
}
}, {$addFields: {
   costo_promedio: {
     $divide: ["$total", "$recamaras"]
   }
}}]```

<br/>

