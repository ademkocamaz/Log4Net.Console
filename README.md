# Log4Net.Console
Log4Net en basit hali ile çalışan konsol uygulaması.
### Yapılacaklar
AssemblyInfo.cs içerisine 

    [assembly: log4net.Config.XmlConfigurator]

App.config içerisine

    <configSections>
        <section name="log4net" type="log4net.Config.Log4NetConfigurationSectionHandler, log4net" />
    </configSections>
    <appSettings>
        <add key="log4net.Config.Watch" value="True"/>
        <add key="log4net.Internal.Debug" value="False"/>
    </appSettings>
    <log4net>
        <appender name="RollingFileAppender" type="log4net.Appender.RollingFileAppender">
            <file value="log.txt" />
            <appendToFile value="true" />
            <rollingStyle value="Size" />
            <maxSizeRollBackups value="10" />
            <maximumFileSize value="250KB" />
            <staticLogFileName value="true" />
            <layout type="log4net.Layout.PatternLayout">
                <conversionPattern value="%date [%thread] %-5level %logger [%property{NDC}] - %message%newline" />
            </layout>
        </appender>
        <root>
            <level value="ALL" />
            <appender-ref ref="RollingFileAppender" />
        </root>
    </log4net>


Program.cs içerisine

private static readonly ILog log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);
