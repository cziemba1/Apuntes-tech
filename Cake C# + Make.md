# Cake C# + Make

Created: Jul 30, 2020 11:44 PM
Reviewed: No

Script Cake ⇒ Parse ⇒ Compile ⇒ Run = Cake.Core.dll + Cake.Common.dll

Task: unit of work. Contain instructions to be executed in a specific order. Acomplish one thing

```csharp
//Pasar el nombre del task que correremos primero como script argument:
var value = Argument("Name", "DefaultValue");
Task("Name") //name
	.IsDependentOn("Another name") // a veces los taks dependen de otros para ejecutarse
	.Does(()=> //action
{
	//work
});
//Estos metodos siempre devuelven el mismo objeto
RunTarget("Name"); // el task que va a correr primero o RunTarget(value);
```

Aliases: Task, IsDependentOn, RunTarget, Argument,

.ContinueOnError(); ⇒ el script se ejecutara aunque haya errores

.ReportError(exception ⇒{}; ⇒ error handling

.OnError();

```csharp
Setup(CakeContext context =>
{
 //Before the first task
	
});
Teardown(CakeContext context =>
{
//After the last task
});

TaskSetup(CakeContext context, CakeTask task) =>
{
 //Before the first task
});
TaskTeardown(CakeContext context, CakeTask task) =>
{
//After the last task
});
```

Context:

```csharp
Task("Name") //name
	.Does(()=> 
{
	var workingDir = Context.Environment.WorkingDirectory;
	Context.Log.Write(
	Verbosity.Diganostic
	LogLevel.Verbose,
	"Working Directory: {0}, workingDir");

	//Este metodo tambien viene con un aliases. Otra forma de escribirlo:
	var workingDir = Context.Environment.WorkingDirectory;
	Verbose("Working Directory: {0}, workingDir");
});
```

![Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled.png](Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled.png)

![Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled%201.png](Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled%201.png)

![Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled%202.png](Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled%202.png)

![Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled%203.png](Cake%20C#%20+%20Make%206de78ef571084471a0d47584bbed2ead/Untitled%203.png)