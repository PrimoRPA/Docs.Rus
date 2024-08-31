# События

Таблица со всеми событиями, которые фиксируются в Primo RPA AI Server, приведены в таблице ниже.

| Название                                  |  Код  | Описание                          |
| ----------------------------------------- | ----- | --------------------------------- |
| InferenceRequestAccepted                  | 100   |                                   |
| InferenceRequestSentForProcessingSuccess  | 101   |                                   |
| InferenceRequestSentForProcessingError    | 102   |                                   |
| InferenceRequestNoAgent                   | 103   |                                   |
| InferenceRequestStartPipeline             | 104   |                                   |
| InferenceRequestDownloadImgFileSuccess    | 105   |                                   |
| InferenceRequestDownloadImgFileError      | 106   |                                   |
| InferenceRequestDownloadMarkingFileSuccess | 107  |                                   |
| InferenceRequestDownloadMarkingFileError  | 108   |                                   |
| InferenceRequestProcessedSuccess          | 109   |                                   |
| InferenceRequestProcessedError            | 110   |                                   |
| InferenceRequestResultTransferred         | 111   |                                   |
| InferenceRequestNoLicensedAgent           | 112   |                                   |
| InferenceProcessCreated                   | 200   |                                   |
| InferenceProcessRemoved                   | 201   |                                   |
| InferenceProcessDisabled                  | 202   |                                   |
| InferenceProcessEnabled                   | 203   |                                   |
| InferenceProcessStarted                   | 204   |                                   |
| InferenceProcessStoped                    | 205   |                                   |
| InferenceProcessSentToLaunch              | 206   |                                   |
| InferenceProcessSentToStop                | 207   |                                   |
| InferenceProcessStartingError             | 208   |                                   |
| InferenceProcessStoppingError             | 209   |                                   |
| InferenceProcessTemplateCreated           | 300   |                                   |
| InferenceProcessTemplateUpdated           | 301   |                                   |
| InferenceProcessTemplateRemoved           | 302   |                                   |
| AgentCreated                              | 400   |                                   |
| AgentUpdated                              | 401   |                                   |
| AgentRemoved                              | 402   |                                   |  
| AgentDisabled                             | 403   |                                   | 
| AgentEnabled                              | 404   |                                   | 
| AgentAutoDisabled                         | 405   |                                   | 
| ScriptCreated                             | 500   |                                   | 
| ScriptUpdated                             | 501   |                                   | 
| ScriptRemoved                             | 502   |                                   | 
| LicenseAdded                              | 601   |                                   | 
| LicenseDeleted                            | 602   |                                   | 
| LicenseDownloaded                         | 603   |                                   | 
| LicenseRevoked                            | 604   |                                   | 
| LicenseRevokeReplaced                     | 605   |                                   | 
| LicenseRequested                          | 606   |                                   | 
| LicenseReplaceRequested                   | 607   |                                   | 
| LicenseToTenantAdded                      | 608   |                                   | 
| LicenseDeactivated                        | 609   |                                   | 
| LicenseActivated                          | 610   |                                   | 
| Login                                     | 2001  |                                   | 
| LoginUserNotExist                         | 2002  |                                   | 
| LoginUserLocked                           | 2003  |                                   | 
| LoginUserUnauthorized                     | 2004  |                                   | 
| LoginUserUnauthorizedAD                   | 2005  |                                   |  
| LoginUserNoRightsGroupAD                  | 2006  |                                   |  
| LogOut                                    | 2007  |                                   |  
| LoginUserExpired                          | 2008  |                                   |  
| ProjectCreated                            | 3000  |                                   |  
| ProjectUpdated                            | 3001  |                                   |  
| ProjectRemoved                            | 3002  |                                   |  
| ProjectDataImgCreated                     | 4000  |                                   |  
| ProjectDataImgUpdated                     | 4001  |                                   |  
| ProjectDataImgRemoved                     | 4002  |                                   |  
| ProjectDataImgArchiveUploaded             | 4003  |                                   |  
| ProjectDataImgCreateError                 | 4004  |                                   |  
| MarkingSchemeCreated                      | 5000  |                                   |  
| MarkingSchemeUpdated                      | 5001  |                                   |  
| MarkingSchemeRemoved                      | 5002  |                                   |  
| MarkingFieldCreated                       | 6000  |                                   |  
| MarkingFieldUpdated                       | 6001  |                                   |   
| MarkingFieldRemoved                       | 6002  |                                   |   
| MarkingFieldTypesUpdated                  | 6003  |                                   |   
| MarkingFieldColumnsUpdated                | 6004  |                                   |   




	FolderCreated = 7000,
    FolderUpdated = 7001,
    FolderRemoved = 7002,
    FolderResubordination = 7003,
    FolderMoveObjects = 7004,
    FolderGrantUserFolders = 7005,
    FolderGrantFolderUsers = 7006,

    RoleCreated = 8000,
    RoleUpdated = 8001,
    RoleRemoved = 8002,
    RoleAssignAdGroups = 8003,
    RoleAssignPermissions = 8004,

    UserCreated = 9000,
    UserUpdated = 9001,
    UserRemoved = 9002,
    UserRolesAssigned = 9003,
    UserPasswordChanged = 9004,
    UserEnabled = 9005,
    UserDisabled= 9006,

    ModelTemplateCreated = 10000,
    ModelTemplateUpdated = 10001,
    ModelTemplateRemoved = 10002,

    MarkingCreateOrEdit = 11000,
    MarkingRemoved = 11001,
    MarkingMovedToDataSet = 11002,

    DataSetCreated = 12000,
    DataSetUpdated = 12001,
    DataSetRemoved = 12002,
	DataSetArchivateStarted = 12003,
    DataSetArchivateCompletedSuccess = 12004,
    DataSetArchivateCompletedError = 12005,
    DataSetArchivateProgress1 = 12006,
    DataSetArchivateProgress2= 12007,
    DataSetArchivateCompletedTimeout = 12008,
    DataSetArchiveUploaded = 12009,
    DataSetArchiveImportSucceed = 12010,
    DataSetArchiveImportFailed = 12011,

	ModelTypeCreated = 13000,
    ModelTypeUpdated = 13001,
    ModelTypeRemoved = 13002,

	ModelCreated = 14000,
    ModelUpdated = 14001,
    ModelRemoved = 14002,
    ModelDownloadSuccess = 14003,
    ModelDownloadError = 14004,

    TrainProcessCreated = 15000,
    TrainProcessRemoved = 15001,
    TrainProcessDisabled = 15002,
    TrainProcessEnabled = 15003,

    TrainProcessSendToStart = 15004,
    TrainProcessStarted = 15005,        
    
    TrainProcessSendToStop = 15006,
    TrainProcessStopedSuccess = 15007,
    TrainProcessStopedError = 15008,

    TrainProcessStartPipeline = 15100,
    TrainProcessEmergencyShutdown = 15101,
	TrainProcessStartFileStoragePrepareSuccess = 15200,
    TrainProcessStartFileStoragePrepareError = 15201,
    TrainProcessStartDownloadScriptSuccess = 15300,
    TrainProcessStartDownloadScriptError = 15301,
    TrainProcessStartDownloadModelTemplateSuccess = 15400,
    TrainProcessStartDownloadModelTemplateError = 15401,
    TrainProcessStartUnzipModelTemplateSuccess = 15402,
    TrainProcessStartUnzipModelTemplateError = 15403,
    TrainProcessStartDownloadModelSuccess = 15500,
    TrainProcessStartDownloadModelError = 15501,
    TrainProcessStartUnzipModelSuccess = 15502,
    TrainProcessStartUnzipModelError = 15503,
    TrainProcessStartDownloadDataSetSuccess = 15600,
    TrainProcessStartDownloadDataSetError = 15601,
    TrainProcessStartUnzipDataSetSuccess = 15602,
    TrainProcessStartUnzipDataSetError = 15603,
    TrainProcessStartDownloadTestDataSetSuccess = 15620,
    TrainProcessStartDownloadTestDataSetError = 15621,
    TrainProcessStartDownloadUnzipTestDataSetSuccess = 15622,
    TrainProcessStartDownloadUnzipTestDataSetError = 15623,
	TrainProcessStartCompletedSuccess = 15700,
    TrainProcessStartCompletedError = 15701,

	TrainProcessCompletedSuccess = 15800,
    TrainProcessCompletedError = 15801,

	TrainProcessTimeout = 15800,

    TrainProcessMetricsReceived = 15900,

	TrainProcessTemplateCreated = 16000,
    TrainProcessTemplateUpdated = 16001,
    TrainProcessTemplateRemoved = 16002,

	PipelineCreated = 17000,
    PipelineUpdated = 17001,
    PipelineRemoved = 17002,

    InferenceProcessStartPipeline = 18100,
    InferenceProcessEmergencyShutdown = 18101,
    InferenceProcessStartFileStoragePrepareSuccess = 18200,
    InferenceProcessStartFileStoragePrepareError = 18201,
    InferenceProcessStartDownloadScriptSuccess = 18300,
    InferenceProcessStartDownloadScriptError = 18301,
    InferenceProcessStartDownloadModelSuccess = 18500,
    InferenceProcessStartDownloadModelError = 18501,
    InferenceProcessStartUnzipModelSuccess = 18502,
    InferenceProcessStartUnzipModelError = 18503,
    InferenceProcessStartDownloadMarkingSchemeSuccess = 18600,
    InferenceProcessStartDownloadMarkingSchemeError = 18601,
    InferenceTestProcessStartDownloadDataSetSuccess = 18700,
    InferenceTestProcessStartDownloadDataSetError = 18701,
    InferenceTestProcessStartUnzipDataSetSuccess = 18702,
    InferenceTestProcessStartUnzipDataSetError = 18703,
	InferenceProcessStartCompletedSuccess = 18800,
    InferenceProcessStartCompletedError = 18801,
    InferenceTestProcessTransferEvaluationResultSuccess = 18900,
	InferenceTestProcessTransferBboxSuccess = 18920,
    InferenceTestProcessCompletedSuccess = 18940,
	InferenceTestProcessCompletedError = 18960,

	AgentLogDataReceived = 19000,
}
