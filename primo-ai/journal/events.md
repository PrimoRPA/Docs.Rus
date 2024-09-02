# События

Все события, которые фиксируются в Primo RPA AI Server, приведены в таблице ниже.

Список событий может измениться в следующих версиях Primo RPA AI Server.

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
| 7000  | FolderCreated                             |                                   |   
| 7001  | FolderUpdated                             |                                   |   
| 7002  | FolderRemoved                             |                                   |  
| 7003  | FolderResubordination                     |                                   |  
| 7004  | FolderMoveObjects                         |                                   |  
| 7005  | FolderGrantUserFolders                    |                                   |  
| 7006  | FolderGrantFolderUsers                    |                                   |  
| 8000  | RoleCreated                               |                                   |  
| 8001  | RoleUpdated                               |                                   |  
| 8002  | RoleRemoved                               |                                   |       
| 8003  | RoleAssignAdGroups                        |                                   |    
| 8004  | RoleAssignPermissions                     |                                   |    
| 9000  | UserCreated                               |                                   |    
| 9001  | UserUpdated                               |                                   |  
| 9002  | UserRemoved                               |                                   |     
| 9003  | UserRolesAssigned                         |                                   |     
| 9004  | UserPasswordChanged                       |                                   |   
| 9005  | UserEnabled                               |                                   |  
| 9006  | UserDisabled                              |                                   |  
| 10000 | ModelTemplateCreated                      |                                   |  
| 10001 | ModelTemplateUpdated                      |                                   |  
| 10002 | ModelTemplateRemoved                      |                                   |  
| 11000 | MarkingCreateOrEdit                       |                                   |  
| 11001 | MarkingRemoved                            |                                   |  
| 11002 | MarkingMovedToDataSet                     |                                   |      
| 12000 | DataSetCreated                            |                                   |   
| 12001 | DataSetUpdated                            |                                   |   
| 12002 | DataSetRemoved                            |                                   |   
| 12003 | DataSetArchivateStarted                   |                                   |   
| 12004 | DataSetArchivateCompletedSuccess          |                                   |   
| 12005 | DataSetArchivateCompletedError            |                                   |
| 12006 | DataSetArchivateProgress1                 |                                   |
| 12007 | DataSetArchivateProgress2                 |                                   |
| 12008 | DataSetArchivateCompletedTimeout          |                                   |
| 12009 | DataSetArchiveUploaded                    |                                   |
| 12010 | DataSetArchiveImportSucceed               |                                   |
| 12011 | DataSetArchiveImportFailed                |                                   |
| 13000 | ModelTypeCreated                          |                                   |
| 13001 | ModelTypeUpdated                          |                                   |
| 13002 | ModelTypeRemoved                          |                                   |
| 14000 | ModelCreated                              |                                   |
| 14001 | ModelUpdated                              |                                   |
| 14002 | ModelRemoved                              |                                   |
| 14003 | ModelDownloadSuccess                      |                                   |
| 14004 | ModelDownloadError                        |                                   |
| 15000 | TrainProcessCreated                       |                                   |
| 15001 | TrainProcessRemoved                       |                                   |
| 15002 | TrainProcessDisabled                      |                                   |
| 15003 | TrainProcessEnabled                       |                                   |
| 15004 | TrainProcessSendToStart                   |                                   |
| 15005 | TrainProcessStarted                       |                                   |
| 15006 | TrainProcessSendToStop                    |                                   |
| 15007 | TrainProcessStopedSuccess                 |                                   |
| 15008 | TrainProcessStopedError                   |                                   |
| 15100 | TrainProcessStartPipeline                 |                                   |
| 15101 | TrainProcessEmergencyShutdown             |                                   |
   
    


    
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
