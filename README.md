# MAS-WoT_productionCell

This project represents a production cell within an Industry 4.0 company.  
It has three execution modes: manual, automatic, and MAS (Multi-Agent System).  
It is implemented in Java and JavaFX, and integration with MAS is handled through JaCaMo.  
In addition, the project includes a RESTful API interface and implements the Web of Things (WoT) through the concepts of Thing and Thing Description.

## The main features of the system include:

- Multi-Agent System: Management of autonomous agents that communicate and collaborate to handle the production flow.

- Thing Description: Object descriptions, called Thing Descriptions, are stored in `.json` files. Agents request these descriptions initially to acquire the properties of objects. Before performing any action on an object, agents verify that the action is present in the Thing Description, ensuring that all interactions comply with the defined specifications.

- HTTP Communication: Implementation of HTTP requests to obtain an object’s Thing Description and to perform actions based on the received Thing Descriptions. Authorization token management is implemented to ensure the security of operations.

- JavaFX Interface: Provides real-time visualization of the production cell simulation, allowing users to intuitively monitor the system’s status and operations.

- Malfunction Handling: Each component of the production cell is equipped with an indicator light showing its status: Red for the component turned off, Green for operational. Specifically for MAS execution, occasionally some lights may turn Yellow, indicating a malfunction of that particular component. This is useful for studying fault management and agent interaction when components experience problems.

## Execution requirements:

- JaCaMo (for MAS execution only):  
  The Multi-Agent System framework used in the project.  
  Installation and configuration instructions for JaCaMo are available at: https://jacamo-lang.github.io/getting-started

- Java:  
  Version 17 or later, available at: https://www.oracle.com/java/technologies/downloads/

- Gradle:  
  Gradle version 8.7 is included in the project’s GitHub repository.  
  No separate Gradle installation is needed, as you can use the included Gradle Wrapper (`gradlew` for Unix/Linux/macOS, `gradlew.bat` for Windows).

### Execution:

To start the system, execution begins from the `Launcher` class, which starts the user interface. Depending on the selected mode (automatic, manual, or MAS), the process is handled automatically.

Automatic or Manual mode:  
The user interface allows choosing between automatic or manual operation modes. The system is configured to manage these modes without further manual intervention.

To run the MAS without the interface, you can use the following commands in the shell from the directory:  
`/productioncellSimulator/src/main/resources/mas`:

Windows:
```
cmd.exe /c gradlew run
```

Unix-like:
```
./gradlew run
```

MAS (Multi-Agent System) mode:  
When MAS mode is selected, the system detects the operating system in use and uses the appropriate Gradle command to start the MAS. In addition, the necessary servers are initialized for communication between agents and for managing the Thing Descriptions.
