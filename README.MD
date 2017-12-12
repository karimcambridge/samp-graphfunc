# SA-MP Graph Func

This include makes it easier to add shapes/graphs and other sorts of graphics to your server.

As long as you have an algorithm for a shape it can be implemented easy with this.

## Original post on SA-MP Forums

	http://forum.sa-mp.com/showthread.php?t=253778

# Resources

## Functions:

```
native Graph:GRAPHIC::Create(Float:x, Float:y, Float:x_min, Float:y_min, Float:x_max, Float:y_max);
native GRAPHIC::XYAxisColor(Graph:_id, _x_color, _y_color);
native GRAPHIC::UseBackground(Graph:_id, use);
native GRAPHIC::BackgroundColor(Graph:_id, color);
native GRAPHIC::GRAPHIC::AddPoint(Graph:_id, Float:x, Float:y, color);
native GRAPHIC::ShowForPlayer(playerid, Graph:_id);
native GRAPHIC::HideForPlayer(playerid, Graph:_id);
native GRAPHIC::ShowForAll(Graph:_id);
native GRAPHIC::HideForAll(Graph:_id);
native GRAPHIC::Update(Graph:_id, playerid = INVALID_PLAYER_ID);
native GRAPHIC::Destroy(Graph:_id);
native GRAPHIC::OtherXYAxis(oper, playerid, Graph:_id, xAxis, yAxis);
```

## Callbacks:

```forward GRAPHIC::Init() // Automatically forwarded in the include ```

This callback should be use to create each graph, for example:

```
new
		Graph:MY_GRAPH;

	public
		GRAPHIC::Init()
	{
		MY_GRAPH = GRAPHIC::Create(200.0, 250.0, -50, -50, 50, 50);
		GRAPHIC::XYAxisColor(MY_GRAPH, 0xFFFFFF55, 0xFFFFFF55);

		GRAPHIC::UseBackground(MY_GRAPH, 1);
		GRAPHIC::BackgroundColor(MY_GRAPH, 0x00000033);

		GRAPHIC::AddPoint(MY_GRAPH, 50,  50, 0x25478588);

		// other graphic creations ..

		return 1;
	}
```

## Restrictions:

There are some sense restrictions when creating a graphs.
You can NOT create graphs in this terms:

```
x-Min, y-Min, x-Max and y-Max all equal to 0
x-Min and x-Max both equal to 0
y-Min and y-Max both equal to 0
```