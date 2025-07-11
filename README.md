# Agent4J

**Agent4J** is a lightweight Java library that simplifies the creation and orchestration of GenAI agents. Using a set of powerful annotations (`@Agent`, `@Tool`, `@Operator`) and the Java Reflection API, Agent4J lets you declaratively define agents, tools, and their operations for intelligent and modular AI-driven systems.

## Features

- **Declarative Agent Definition:** Use simple annotations to mark classes and methods as agents, tools, or operators.
- **Reflection-based Discovery:** Agents and their tools are automatically discovered and wired at runtime.
- **Flexible Orchestration:** Easily manage interactions between agents and compose complex workflows.
- **Plug-and-Play Integration:** No invasive frameworks—just add the dependency and annotate your code.

## Installation

Add Agent4J to your project using Maven:

```xml
<dependency>
  <groupId>org.agent4j</groupId>
  <artifactId>agent4j-core</artifactId>
  <version>1.0.0</version>
</dependency>
```
Or Gradle:

```groovy
implementation 'com.yourorg:agent4j:0.1.0'
```

## Quick Start

1. Annotate your classes and methods
```java
import agent4j.annotations.Agent;
import agent4j.annotations.Tool;
import agent4j.annotations.Operator;

@Agent(name = "MathAgent")
public class MathAgent {

    @Tool(description = "Basic addition tool")
    public int add(int a, int b) {
        return a + b;
    }

    @Operator
    public int square(int x) {
        return x * x;
    }
}
```

2. Initialize the Agent Orchestrator
```java
import agent4j.AgentOrchestrator;

public class Main {
    public static void main(String[] args) {
        AgentOrchestrator orchestrator = new AgentOrchestrator("com.yourorg.agents");
        MathAgent mathAgent = orchestrator.getAgent(MathAgent.class);

        int sum = mathAgent.add(2, 3);
        int squared = mathAgent.square(4);

        System.out.println("Sum: " + sum);           // Sum: 5
        System.out.println("Squared: " + squared);   // Squared: 16
    }
}
```

## Annotations
- @Agent — Marks a class as an agent.
- @Tool — Marks a method as a tool the agent can use.
- @Operator — Marks a method as a composable operation within the agent.

## Use Cases
- Modular GenAI agent construction
- Dynamic orchestration of AI tools and agents
- Automated discovery of agent capabilities for LLMs, chatbots, and more

## Contributing
Contributions, issues, and feature requests are welcome!
Feel free to check the issues page.
