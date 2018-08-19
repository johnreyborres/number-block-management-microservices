# Number Block Management Microservice Design
This is a detailed design for a microservice which does number block management from a telco perspective.

# Microservices
##### Numbers microservice
This microservice will focus mainly on the management of numbers. The telco operator will manage the creation and updates of the numbers data.
        
##### Tracking microservice
This microservice will focus mainly on the tracking of numbers. Tracking includes the current status of the number and the history of statuses on the lifecyle of the numbers.
        
# Logical design
The logical design containing the abstract representation of the data is described in the schema design below.

**Numbers**
| Field | Data Type | Description |
| --- |--- |--- |
| id | int | Primary key |
| number | varchar | The number |
| created_at | datetime | Created at timestamp |
| updated_at | datetime | Updated at timestamp |

**Numbers History**
| Field        	    | Data Type     | Description  			|
| -------------     |-------------  | ----------------------|
| id      		    | int 			| Primary key |
| number_id      	| int           | Foreign key of numbers table |
| number_status_id  | int           | Foreign key of number status table |
| is_current      	| boolean       | The indicator of the current status |
| updated_by_id     | int           | Foreign key of user who does the update |
| remarks      	    | varchar       | Remarks of status change |
| created_at 	    | datetime      | Created at timestamp |
| updated_at 	    | datetime      | Updated at timestamp |

**Number Statuses**
| Field        	    | Data Type     | Description  			|
| -------------     |-------------  | ----------------------|
| id      		    | int 			| Primary key |
| status_name      	| varchar       | The name of the status |
| status_desc       | varchar       | The description of the status |
| created_at 	    | datetime      | Created at timestamp |
| updated_at 	    | datetime      | Updated at timestamp |

**Users**
| Field        	    | Data Type     | Description  			|
| -------------     |-------------  | ----------------------|
| id      		    | int 			| Primary key |
| name      	    | varchar       | The name of the user |
| created_at 	    | datetime      | Created at timestamp |
| updated_at 	    | datetime      | Updated at timestamp |

# Architectural design
The design of the system architecture is described  [here](https://drive.google.com/file/d/1E_vmjDyL6uIqivGpAwShZ4FOLiI_3QUy/view?usp=sharing). It leverages the use of Amazon Web Services.

# Communication Protocol
The HTTP/S protocol is the most popular way to implement synchronous communication between microservices. For this, RESTful APIs will be the type of API to be exposed to consuming applications using the HTTP as a transport layer. The REST architectural style relies on stateless communication, uniform interfaces, and standard methods.
