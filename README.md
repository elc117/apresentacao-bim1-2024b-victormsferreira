# Código da solução:

```hs
-- Bounding boxes: (xmin, ymin, xmax, ymax)
boundingBoxes :: [(Float, Float, Float, Float)]
boundingBoxes = [ (34.0, 60.0, 200.0, 320.0),
                  (100.0, 150.0, 250.0, 380.0),
                  (300.0, 220.0, 450.0, 450.0) ]

getInvalidBoundingBoxes :: [(Float, Float, Float, Float)] -> [(Float, Float, Float, Float)]
getInvalidBoundingBoxes boxes = filter (\(x1, y1, x2, y2) -> x2 < x1 || y2 < y1) boxes
```

# Exemplos

```hs
ghci> getInvalidBoundingBoxes boundingBoxes 
[]
ghci> getInvalidBoundingBoxes [(1.0,2.0,3.0,4.0),(3.0,4.0,1.0,2.0)]
[(3.0,4.0,1.0,2.0)]
ghci> getInvalidBoundingBoxes [(1.0,2.0,3.0,4.0),(3.0,4.0,1.0,2.0),(5.0,2.0,80.0,1.0),(2.0,2.0,4.0,4.0),(5.0,10.0,10.0,1.0)]
[(3.0,4.0,1.0,2.0),(5.0,2.0,80.0,1.0),(5.0,10.0,10.0,1.0)]
```

# Explicação:

Como queremos uma função que receba uma lista e retorne uma outra lista com elementos que satisfaçam uma condição, a função deve ser definida como `getInvalidBoundingBoxes boxes = filter __ boxes`

Agora precisamos apenas de uma função lambda que verifique se uma bounding box é válida ou não. Uma bounding box é definida por uma tupla da forma `(xmin, ymin, xmax, ymax)`, portanto essa função lambda deve ser algo da forma `(\(xmin, ymin, xmax, ymax) -> ____)`

Agora que temos uma função lambda que recebe os valores da bounding box, apenas é necessário que ela retorne se ela é válida ou não. Essa condição é de que xmin seja maior que xmax, ou que ymin seja maior que ymax. Portanto, a função lambda completa será: `(\(xmin, ymin, xmax, ymax) -> xmin > xmax || ymin > ymax)`

Portanto, a função completa sera `getInvalidBoundingBoxes boxes = filter (\(x1, y1, x2, y2) -> x2 < x1 || y2 < y1) boxes`, e essa função tem o tipo `[(Float, Float, Float, Float)] -> [(Float, Float, Float, Float)]`
