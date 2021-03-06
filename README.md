# ADT - Query the Properties of a Relationship

This sample demonstrates how to query a specific property of a relationship.

Similarly to the way digital twins have properties described, relationships can also have properties. You can query twins based on the properties of their relationships. The Azure Digital Twins query language allows filtering and projection of relationships, by assigning an alias to the relationship within the [JOIN](https://docs.microsoft.com/en-us/azure/digital-twins/reference-query-clause-join) clause.

For the purpose of this sample we will query the following ADT Model: [Example of a simplified Azure Digital Twins Model](https://github.com/RobertEichenseer/AzureDigitalTwins_Models).

![Twin Graph](./images/twin_graph.PNG)

Consider the ```assignedProductionLine``` relationship that was defined with two properties, ```productionManager``` and ```inProduction```. Ensure that the properties are set.

Finally, query the Twin Graph using the query bellow.

```SQL
SELECT T, CT 
FROM DIGITALTWINS T 
JOIN CT RELATED T.assignedProductionLine R 
WHERE T.$dtId = 'ord_Muc_01' 
AND R.inProduction = True
```

The result will be relationships of type ```assignedProductionLine```, associated with the twin  ```ord_Muc_01``` where the property ```inProduction = True```.

![Twin Graph Result](./images/query_result.PNG)
