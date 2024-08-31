# События

Таблица со всеми событиями, которые фиксируются в Primo RPA AI Server, приведены в таблице ниже.

|  Код  | Название                                  | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 100   | InferenceRequestAccepted                  |                                   |
| 101   | InferenceRequestSentForProcessingSuccess  |                                   |
| 102   | InferenceRequestSentForProcessingError    |                                   |
| 103   | InferenceRequestNoAgent                   |                                   |
| 104   | InferenceRequestStartPipeline             |                                   |
| 105   | InferenceRequestDownloadImgFileSuccess    |                                   |
| 106   | InferenceRequestDownloadImgFileError      |                                   |
| 107   | InferenceRequestDownloadMarkingFileSuccess |                                  |
| 108   | InferenceRequestDownloadMarkingFileError  |                                   |
| 109   | InferenceRequestProcessedSuccess          |                                   |
| 110   | InferenceRequestProcessedError            |                                   |
| 111   | InferenceRequestResultTransferred         |                                   |
| 112   | InferenceRequestNoLicensedAgent           |                                   |
| 200   | InferenceProcessCreated                   |                                   |
| 201   | InferenceProcessRemoved                   |                                   |
| 202   | InferenceProcessDisabled                  |                                   |
| 203   | InferenceProcessEnabled                   |                                   |
| 204   | InferenceProcessStarted                   |                                   |
| 205   | InferenceProcessStoped                    |                                   |
| 206   | InferenceProcessSentToLaunch              |                                   |
| 207   | InferenceProcessSentToStop                |                                   |
| 208   | InferenceProcessStartingError             |                                   |
| 209   | InferenceProcessStoppingError             |                                   |
| 300   | InferenceProcessTemplateCreated           |                                   |
| 301   | InferenceProcessTemplateUpdated           |                                   |
| 302   | InferenceProcessTemplateRemoved           |                                   |
| 400   | AgentCreated                              |                                   |
| 401   | AgentUpdated                              |                                   |
| 402   | AgentRemoved                              |                                   |  
| 403   | AgentDisabled                             |                                   | 
| 404   | AgentEnabled                              |                                   | 
| 405   | AgentAutoDisabled                         |                                   | 
| 500   | ScriptCreated                             |                                   | 
| 501   | ScriptUpdated                             |                                   | 
| 502   | ScriptRemoved                             |                                   | 
| 601   | LicenseAdded                              |                                   | 
| 602   | LicenseDeleted                            |                                   | 
| 603   | LicenseDownloaded                         |                                   | 
| 604   | LicenseRevoked                            |                                   | 
| 605   | LicenseRevokeReplaced                     |                                   | 
| 606   | LicenseRequested                          |                                   | 
| 607   | LicenseReplaceRequested                   |                                   | 
| 608   | LicenseToTenantAdded                      |                                   | 
| 609   | LicenseDeactivated                        |                                   | 
| 610   | LicenseActivated                          |                                   | 
| 2001  | Login                                     |                                   | 
| 2002  | LoginUserNotExist                         |                                   | 
| 2003  | LoginUserLocked                           |                                   | 
| 2004  | LoginUserUnauthorized                     |                                   | 
| 2005  | LoginUserUnauthorizedAD                   |                                   |  
| 2006  | LoginUserNoRightsGroupAD                  |                                   |  
| 2007  | LogOut                                    |                                   |  
| 2008  | LoginUserExpired                          |                                   |  
| 3000  | ProjectCreated                            |                                   |  
| 3001  | ProjectUpdated                            |                                   |  
| 3002  | ProjectRemoved                            |                                   |  
| 4000  | ProjectDataImgCreated                     |                                   |  
| 4001  | ProjectDataImgUpdated                     |                                   |  
| 4002  | ProjectDataImgRemoved                     |                                   |  
| 4003  | ProjectDataImgArchiveUploaded             |                                   |  
| 4004  | ProjectDataImgCreateError                 |                                   |  
| 5000  | MarkingSchemeCreated                      |                                   |  
| 5001  | MarkingSchemeUpdated                      |                                   |  
| 5002  | MarkingSchemeRemoved                      |                                   |  
| 6000  | MarkingFieldCreated                       |                                   |  
| 6001  | MarkingFieldUpdated                       |                                   |   
| 6002  | MarkingFieldRemoved                       |                                   |   
| 6003  | MarkingFieldTypesUpdated                  |                                   |   
| 6004  | MarkingFieldColumnsUpdated                |                                   |   




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
