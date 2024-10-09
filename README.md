# Lang-graph

Hello LangGraph
LangGraph is a library for building stateful, multi-actor applications with LLMs, used to create agent and multi-agent workflows.  

Compared to other LLM frameworks, it offers these core benefits: cycles, controllability, and persistence.  

LangGraph allows you to define flows that involve cycles, essential for most agentic architectures, differentiating it from DAG-based solutions.  

As a very low-level framework, it provides fine-grained control over both the flow and state of your application, crucial for creating reliable agents.  



The Simplest Graph  
Let's build a simple graph with 2 nodes and simple edges flow.  
![image](https://github.com/user-attachments/assets/1a60033b-895b-4fe1-a36e-fa45522cc555)


**State**  
First, define the State of the graph.  

The State schema serves as the input schema for all Nodes and Edges in the graph.  


**Nodes**  
Nodes are just python functions.  

The first positional argument is the state, as defined above.  

Because the state is a TypedDict with schema as defined above, each node can access the key, graph_state, with state['graph_state'].  

Each node returns a new value of the state key graph_state.  


**Edges**  
Edges connect the nodes.  

Normal Edges are used if you want to always go from, for example, node_1 to node_2.  





**Graph Construction**  
Now, we build the graph from our components defined above.  

The StateGraph class is the graph class that we can use.  

First, we initialize a StateGraph with the State class we defined above.  

Then, we add our nodes and edges.  
  
We use the START Node, a special node that sends user input to the graph, to indicate where to start our graph.  

The END Node is a special node that represents a terminal node.  

Finally, we compile our graph to perform a few basic checks on the graph structure.  
