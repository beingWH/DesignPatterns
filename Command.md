# 命令模式
## 新建命令接口
所有命令都必须要实现该接口。
```C#
public interface ICommand
{
	void execute();
	string getDescription();
}
```
## 新建调用方类
Invoker对象组织和执行命令。
```C#
public class Invoker
{
	ICommand command;
	ICommand[] commands;
	public Invoker(ICommand command){
		this.command=command;
	}
	public Invoker(ICommand[] commands){
		this.commands=commands;
	}
    public void Action()
    {
        if (commands == null)
        {
            command.execute();
            description = command.getDescription();
        }
        else
        {
            for(int i = 0; i < commands.Count(); i++)
            {
                commands[i].execute();
                description += commands[i].getDescription();
                description += "&";
            }
        }
    }
    public string getDescription()
    {
        return description;
    }
}
```
## 新建命令
```C#
public class MotoRun:ICommand
{
    public void execute()
	{
   	 	DoSomething();
	}
	
	public string getDescription()
	{
    	return "DoSomething";
	}
}
```
## 调用命令
```C#
ICommand command=new MotoRun();
Invoker invoker=new Invoker(command);
invoker.Action();
invoker.getDescription();
```