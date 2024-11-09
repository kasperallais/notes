WIMI
- Subsystem of the PowerShell that provides system administrators with powerful tools for system monitoring
- Consolidate device and application management across corporate networks
- Made up of the following components:
    - WIMI service - Runs automatically at boot and acts as an intermediary between WIMI providers, the WIMI repository, and managing applications
    - Managed objects - Any logical or physical components that can be managed by WIMI
    - WIMI providers - Objects that monitor events/data related to a specific object
    - Classes - Used by the WIMI providers to pass data to the WIMI service
    - Methods - Attached to classes can allow actions to be performed
    - WIMI repository - A database that stores al static data related to the WIMI
    - CIM Object Manager - System that requests data from WIMI providers and returns it to the application requesting it
    - WIMI Consumer - Sends queries to objects via the CIM Object Manager