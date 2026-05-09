# TTS: Train Ticket System

# Development Documentation

## 1. Module Diagram

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/work.png)

## 2. Function Overview
### Users Class
| Function Name | Description | Return Information |
| :-----: | :-----:  | :-----: |
| init | Initialize and create the B+ tree | No return value |
| print_user | Print users | No return value |
| add_user | Add a user | Success or failure |
| login | User login | Success or failure |
| logout | User logout | Success or failure |
| query_profile | Query user information | User information or failure |
| modify_profile | Modify user information | User information or failure |
### Trains Class
| Function Name | Description | Return Information |
| :-----: | :-----:  | :--------: |
| init | Initialize and create the B+ tree | No return value |
| add_train | Add a train | Success or failure |
| release_train | Release a train | Success or failure |
| query_train | Query a specific train on a specific day | Train information or failure |
| delete_train | Delete a train | Success or failure |
| query_ticket | Query direct tickets for a specific day | All matching tickets or failure |
| get_ticket | Query direct tickets after a specific time | The optimal ticket option |
| query_transfer | Query transfer tickets for a specific day | The optimal ticket option or failure |
### Orders Class
| Function Name | Description | Return Information |
| :-----: | :-----:  | :--------: |
| init | Initialize and create the B+ tree | No return value |
| buy_ticket | Buy a ticket for a specific train | Success, waitlist, or failure |
| query_order | Query user orders | All user orders or failure |
| refund_ticket | Refund a ticket | Success or failure |
### Hash_table Class
| Function Name | Description | Return Information |
| :-----: | :-----:  | :--------: |
| hash | Get the hash value of a string | Hash value |

### Connector Class
| Function Name | Description | Return Information |
| :-----: | :-----:  | :--------: |
| init | Initialize the program | No return value |
| work | Main program workflow | No return value |
| clean | Clear all data | No return value |
| exit | Exit the program | No return value |
### Other Functions (Python)
| Function Name | Description | Return Information |
| :-----: | :-----:  | :--------: |
| get_result | Interaction between the Python side and the C++ side | Request result |
| id_check_valid | Check whether the train_id/Username entered by the user is valid | Validation result |
| password_check_valid | Check whether the password entered by the user is valid | Validation result |
| name_check_valid | Check whether the name entered by the user is valid | Validation result |
| check_station_name | Check whether the number of station names entered by the user matches the station count | Validation result |
| check_num | Check whether the price/travel time/stopover time entered by the user is valid | Validation result |
| check_date | Check whether the date selected by the user is valid | Validation result |
| form_date | Convert to the standard date format | Conversion result |
| form_time | Convert to the standard time format | Conversion result |

## 3. File Design
| B+ Tree Name | Purpose |
| :-----: | :-----: |
| bpuser | Records user information |
| bptrain | Records train information |
| bpseat | Records remaining ticket information |
| bpstation | Records station information |
| bpstrain | Records train information for each station passed through |
| bpuorder | Records user order information |
| bptorder | Records waitlisted train order information |

## 4. Team Contributions

| Name | Task |
| :-----: | :-----: |
| Haotian Chu | Webpage design, frontend-backend integration, development manual and user manual writing |
| Yifan Ren | Main backend logic, development manual writing |
| Yang Heng | B+ tree implementation, including cache and file operations, development manual writing |

------

# User Manual


### 1. Download and Installation

* Python and MINGW or another C/C++ compiler are required.
* Run `pip install flask` and install the related third-party libraries.
* Run `git clone`.
* Compile and run all C++ files in the `backend` folder.
* Open a terminal in the `master` directory and run `flask run`.
* Open a browser, Chrome is recommended, and visit "http://127.0.0.1:5000/".

### 2. Registration and Login

* Because you are not logged in, the first visit to the website will route you to the tourist page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/tourist.png)

* Refresh the page, and the train-related image on the page will change randomly.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/tourist2.png)

* Click any operation in the sidebar, and the system will notify you that you have no permission to access it.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/tourist_fail.png)

* Click login to go to the login page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/login.png)

* Click Signup to go to the registration page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/register.png)

* If the input is invalid, a flash message will be displayed above the form.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/register_invalid.png)

* If the input is valid and the registered Username has not been used, registration succeeds and the page redirects to the login page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/register_success.png)

* If the Username already exists, registration fails.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/register_fail.png)

* After a successful login, you will enter the home page and see that the New User count has increased by one.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/index.png)


### 3. Train Operations

* Click Train -> Add in the sidebar to enter the add_train page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/add_train.png)

* Enter train information according to the prompts. If the input is invalid, a flash message will also be displayed.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/add_train_invalid.png)

* Click Train -> Query in the sidebar to enter the query_train page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_train.png)

* If the queried train has not been released yet, you can release or delete it directly on this page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_train_result.png)

* Confirmation step for releasing a train.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_train_release_ing.png)
 
* After release, the train status is displayed as Released.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_train_released.png)

* You can also click Train -> Release in the sidebar to enter the release_train page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/release.png)

* Click Train -> Delete in the sidebar to enter the delete_train page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/delete.png)

### 4. User Operations

* Click User -> Add New User in the sidebar to enter the add_user page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/add_user.png)

* If the input is invalid, a flash message will be displayed above the form.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/add_user_invalid.png)

* Click User -> Query/Modify in the sidebar to enter the query_user page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_user.png)

* If the queried user exists and has a permission level no higher than the current user, the query succeeds and modification is available.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_user_result.png)

* Click Modify to enter the modification page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/modify.png)
### 5. Ticket Operations

* Click Tickets -> Ticket Query in the sidebar to enter the query_tickets page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_ticket.png)

* Results can be output using three different priorities: 'time', 'cost', and 'transfer one and only'. If matching tickets are found, they can be purchased directly.
 
![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_ticket_result.png)

* Click Buy to go to the buy_tickets page. The station names and date will be filled in automatically. You can also click Tickets -> Buy Ticket in the sidebar to enter the buy_tickets page manually.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/query_to_buy.png)

* The purchase result is displayed based on your waitlist preference and the train availability.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/buy_success.png)

### 6. Other Operations

* Click My Order in the sidebar to enter My Orders, where you can refund tickets.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/my_order.png)

* After a successful refund, the order is displayed as Refunded.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/my_order_refunded.png)

* Click Clear in the sidebar to enter the database clearing page.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/clear_all.png)

* Click Clear all data, and the system will ask the user to confirm multiple times.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/clear_warning.png)

* After confirming the clearing operation, you will return to the tourist page and all data will be cleared.

![avatar](https://raw.githubusercontent.com/ixxxMrAnderson/TrainTickets/master/img/clear.png)
