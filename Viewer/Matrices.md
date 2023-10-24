### Transpose Matrix
Used to convert a matrix between row-major order & column-major order.

![](Images/MatrixRowAndColumnMajorOrder.png)

```csharp
public double[] TransposeMatrix(double[] inputMatrix, int width = 4, int height = 4)
{
	double[] result = new double[width * height];

	for (int i = 0; i < height; i++)
	{
		for (int j = 0; j < width; j++)
		{
			double currentValue = inputMatrix[i + (j * width)];
			currentValue = Math.Round(currentValue, 3);
			result[(i * width) + j] = currentValue;
		}
	}

	return result;
}
```

```csharp
public double[,] TransposeMatrix(double[,] inputMatrix, int width = 4, int height = 4)
{
    double[,] result = new double[width, height];

    for (int i = 0; i < height; i++)
    {
        for (int j = 0; j < width; j++)
        {
            result[j, i] = inputMatrix[i, j];
        }
    }

    return result;
}
```

References: [#1](https://en.wikipedia.org/wiki/Transpose), [#2](https://stackoverflow.com/questions/29483660/how-to-transpose-matrix)


## Resources
- [opengl-tutorial](https://www.opengl-tutorial.org/beginners-tutorials/tutorial-3-matrices/)
- [e-verse](https://e-verse.com/blog-build/dealing-with-matrix-tranformations/)
- [Discover three.js](https://discoverthreejs.com/book/first-steps/transformations/)
- [GeeksForGeeks](https://www.geeksforgeeks.org/computer-graphics-3d-rotation-transformations/)
- [Wikipedia](https://en.wikipedia.org/wiki/Transformation_matrix)
