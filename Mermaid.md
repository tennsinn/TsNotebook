# Mermaid

## Graph & Flowchart

Create a main graph.

	graph orientation
		nodes

Or use `flowchart` notation to enable more feature.

	flowchart orientation
		nodes

Create a subgraph inside the main graph or flowchart, name is the optinal attribute.

	subgraph id[name]
		nodes
	end

### Orientation

| Defination | Description   |
| :--------: | :------------ |
|    `TD`    | top to down   |
|    `TB`    | top to bottom |
|    `BT`    | bottom to top |
|    `RL`    | bight to left |
|    `LR`    | left to right |

### Nodes & shapes

*Notes: need exclosed the node text with `"` if it containes any symbols.*
*Notes: wrap the line with notation `\n`.*

|   Defination   | Description                             |
| :------------: | :-------------------------------------- |
|       id       | default node and 'id' will show as text |
|  id`[`text`]`  | node with rectangle box                 |
|  id`(`text`)`  | node with round edges                   |
| id`([`text`])` | stadium-shaped node                     |
| id`[[`text`]]` | node in a subroutine shape              |
| id`[(`text`)]` | node in a cylindrical shape             |
| id`((`text`))` | node in the form of a circle            |
|  id`>`text`]`  | node in an asymetric shape              |
|  id`{`text`}`  | rhombus node                            |
| id`{{`text`}}` | hexagon node                            |
| id`[/`text`/]` | parallelogram node                      |
| id`[\`text`\]` | parallelogram alt node                  |
| id`[/`text`\]` | trapezoid node                          |
| id`[\`text`/]` | trapezoid alt node                      |

### Links between nodes

*Notes: statements with a semicolon is optional after release 0.2.16.*
*Notes: without a space between node and link is also valid.*

|  Defination   | Description                  |
| :-----------: | :--------------------------- |
|     `---`     | open link                    |
|     `-->`     | link with arrow head         |
| `--`text`-->` | text on link with arrow head |
| `-->|`text`|` | ^^                           |
|    `-.->`     | dotted link with arrow head  |
|     `==>`     | thick link with arrow head   |

### Chaining of links

Make a chaining links in the same line.

	A --> B --> C

Declare multiple nodes links in the same line.

	A --> B & C --> D
	A & B --> C & D

### New arrow types with flowchart notation

| Defination | Description     |
| :--------: | :-------------- |
|   `--o`    | dot head        |
|   `--x`    | cross head      |
|   `<-->`   | dual arrow head |
|   `o--o`   | dual dot head   |
|   `x--x`   | dual cross head |

### Interaction

Bind a click event to a node. Can lead to callback script function or a link

	click node_id callbackFunc "tooltip"
	click node_id "link_addr" "link_title"

	<script>
		var callbackFunc = function(){
		}
	</script>

*Note: this functionality onl can be used with the settings `securityLevel='loose'`.

	<script>
		var config = {
			securityLevel:'loose',
		};
		mermaid.initialize(config);
	</script>

### Comments

Start with `%%` to create a inline comment inside a mermaid graph.

### Styling and classes

#### Styling links

Use `linkStyle` notation to apply the styles to a link by the num which is ordered by the time when the link defined in the graph and started from 0.

	linkStyle link_num css_styles

#### Styling a node

Use `style` notation to apply the styles to the node by node id.

	style node_idclassDef default

Define a style class with the notation `classDef`, and apply the class to the node with the notation `class` or `:::` operator next to the node id.

	classDef class_name css_styles
	class node_id class_name
	class node_id1, node_id2 class_name

	A:::class_name --> B
	classDef class_name css_styles

Can also use CSS to apply the styles to the node.

	.class > rect {}

The default class will apply to all the classes withou specific class definations.

	classDef default css_styles

### Configuration

The redered width can be setted with the definition `mermaid.flowchartConfig`.

	mermaid.flowchartConfig = {
		width: 100%
	}

## Sequence Diagram

*Notes: the word **end** should be enclosed with `()`, `""`, `{}` or `[]`, or it may be prased to close the diagram.*

Create a sequence diagram.

	sequenceDiagram
		messages

### Participants and Aliases

The participants will be auto created when define the messages and it will be rendered in order of the appearance.  
It also can be defined in specific order with the notation `participant` and can set the alias if needed.

	participant id as alias

### Messages

Create a message with a arrow line between two actors.

*Notes: the space between actor and line is optinal.*

	actor_id1 ->> actor_id2: message

|  Type  | Description                                 |
| :----: | :------------------------------------------ |
|  `->`  | solid line without arrowhead                |
| `-->`  | dotted line without arrowhead               |
| `->>`  | solid line with arrowhead                   |
| `-->>` | dotted line without arrowhead               |
|  `-x`  | solid line with a cross at the end (async)  |
| `--x`  | dotted line with a cross at the end (async) |

### Activations

Using the notation `activate` and `deactivate` or a shortcut notation by appending `+`/`-` suffix to the message arrow can activate or deactivate an actor.  
And the activations can be stacked for same actor.

	activate actor_id2
	actor_id1 ->>+ actor_id2: message1

	deactivate actor_id2
	actor_id2 ->>- actor_id1: message2

### Notes

Notes can be added to the diagram with the notation `Note`, and can use attribute `right of`, `left of` or `over` to define the note position to the actor or actors.

	Note right of actor_id: note_content
	Note left of actor_id: note_content
	Note over actor_id1,actor_id2: note_content

### Loops

Can express loop by using the notation `loop`.

	loop loop_text
		messages
	end

### Alt

Can express alternative paths with the notation `alt`.  
And the notation `opt` can be added for the sequence that is optional.

	alt describing_text
		messages
	else
		messages
	end
	opt extra_response
		messages
	end

### Parallel

Can show actions happening in parallel with the notation `par`.  
And the parallel code can be nested.

	par action1
		messages
	and action2
		messages
	and actionN
		messages
	end

### Comments

The individual line prefaced with notation `%%` will be parsed as comments

	%% comments

### Sequence Numbers

The sequence number which attached to each arrow in the diagram can be enabled by the configuration.

	<script>
		mermaid.initialize({
			sequence: { showSequenceNumbers: true },
		});
	</script>

It can also be turned on via the code `autonumber`.

	sequenceDiagram
		autonumber
		messages

### Styling

Can change the diagram styles by set the css styles with some certain classes.

|    Class     | Description                                                |
| :----------: | :--------------------------------------------------------- |
|    actor     | style for the actor box at the top of the diagram          |
|  text.actor  | styles for text in the actor box at the top of the diagram |
|  actor-line  | the vertical line for an actor                             |
| messageLine0 | styles for the solid message line                          |
| messageLine1 | styles for the dotted message line                         |
| messageText  | defines styles for the text on the message arrows          |
|   labelBox   | defines styles label to left in a loop                     |
|  labelText   | styles for the text in label for loops                     |
|   loopText   | styles for the text in the loop box                        |
|   loopLine   | defines styles for the lines in the loop box               |
|     note     | styles for the note box                                    |
|   noteText   | styles for the text on in the note boxes                   |

### Configuration

Some configurations like the margins can be adjusted by defining `mermaid.sequenceConfig` in script.

	mermaid.sequenceConfig = {
		param1: value1,
		param2: value2
	}

|       Param       | Description                                                                |         Default value          |
| :---------------: | :------------------------------------------------------------------------- | :----------------------------: |
|  diagramMarginX   |                                                                            |                                |
|  diagramMarginY   |                                                                            |                                |
|   boxTextMargin   |                                                                            |                                |
|   mirrorActors    | turns on/off the rendering of actors below the diagram as well as above it |             false              |
|  bottomMarginAdj  | adjusts how far down the graph ended                                       |               1                |
|   actorFontSize   | sets the font size for the actor's description                             |               14               |
|  actorFontFamily  | sets the font family for the actor's description                           |   "Open-Sans", "sans-serif"    |
|  actorFontWeight  | sets the font weight for the actor's description                           |   "Open-Sans", "sans-serif"    |
|    noteMargin     |                                                                            |                                |
|   noteFontSize    | sets the font size for actor-attached notes                                |               14               |
|  noteFontFamily   | sets the font family for actor-attached notes                              | "trebuchet ms", verdana, arial |
|  noteFontWeight   | sets the font weight for actor-attached notes                              | "trebuchet ms", verdana, arial |
|     noteAlign     | sets the text alignment for text in actor-attached notes                   |             center             |
|   messageMargin   |                                                                            |                                |
|  messageFontSize  | sets the font size for actor<->actor messages                              |               16               |
| messageFontFamily | sets the font family for actor<->actor messages                            | "trebuchet ms", verdana, arial |
| messageFontWeight | sets the font weight for actor<->actor messages                            | "trebuchet ms", verdana, arial |

## Class Diagram

## Pie Chart

Start with the notation `pie` can create a pie chart.

The notation `title` which is optinal can define the title of the chart.

The label for a section should be enclosed in `""`, and notation `:` will be a separator for the label and the value.  
*Notes: the value support upto two decimal places.*

	pie
		title pie_chart_title
		"label" : value
