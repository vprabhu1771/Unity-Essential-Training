```
https://www.youtube.com/watch?v=AUjw7dvVhOw
```

# Add Custom Menu To Unity Editor

`CustomMenu.cs`

```csharp
using UnityEditor;
using UnityEngine;

public class CustomMenu : Editor
{
	[MenuItem("Custom Menu %&a")]
	private static void DisplayAll()
	{
		
	}
}
```