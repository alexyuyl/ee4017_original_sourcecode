#EE4017 Group 10 Source Code

This project consists of 4 .py file, each representing one single user:  

    blockchain1.py => user1 => 1000
    blockchain2.py => user2 => 2000
    blockchain3.py => user3 => 3000
    blockchain4.py => user4 => 4000
  
To start the project, execute the files desired.  
This will start a local server for corresponding user.  

In this project, we used FASTAPI built-in interface.  

The HTTP server allows direct query for accessing.  
However, navigate the functions through API is suggested. 

To access:  

    http://0.0.0:{port}/docs (for MAC)

    http://127.0.0.1:{port}/docs or
    http://127.0.0.1:{port}/redoc (for Windows)

##API User Guide:

###Step 1: @app method 'full_chain'

@para = None

Click the 'try it out' button, and then hit execute.  

![full chain 'try it out'](assets/def_full_chain.png)
![full chain 'execute'](assets/def_full_chain_execute.png)
Take blockchain1.py as example:  

    This will create the genisis block as the starting point. 
    As it can be seen in the figure, the chain will list
        - The length of chain
        - The information of each block inside the chain

![full chain 'result'](assets/def_full_chain_results.png)

###Step 2: @app method 'get_pub_key'

@para = None

Click the 'try it out' button, and then hit execute

![get pub key 'try it out'](assets/def_get_pub_key.png)
![get pub key 'execute'](assets/def_get_pub_key_execute.png)

Take blockchain1.py as example:

    This will retrieve the unique public key from the user,  
    which is generated along with the private key at the beginning.
    The public key will be required in other functions later.

![get pub key 'result'](assets/def_get_pub_key_results.png)

###Step 3: @app method 'get balance'

@para = None

Click the 'try it out' button, and then hit execute

![get balance 'try it out'](assets/def_get_balance.png)
![get balance 'execute'](assets/def_get_balance_execute.png)

Take blockchain1.py as example:

    Each new user starts with 50 Bitcoins.
    The defition will return the user's wallet balance.

![get balance 'result'](assets/def_get_balance_results.png)

###Step 4: @app method 'mine'

@para = None

Click the 'try it out' button, and then hit execute

![mine 'try it out'](assets/def_mine.png)
![mine 'execute'](assets/def_mine_execute.png)

Take blockchain1.py as example:

    This is the process of adding new block.
    The new block will contain certain information
        - Index of that block
        - The public key of the miner
        - The reward for mining
        - The hash value of the previous block
        - The hash value of that block

![mine 'result'](assets/def_mine_results.png)

###Step 4: @app method 'new_transaction'

@para = sender, recipient, amount

This definition takes in 3 parameters:
    
    sender => public key of the sender
    recipient => public key of the recipient
    amount => numeric input, either string or decimal

Click the 'try it out' button.
![new transaction 'try it out'](assets/def_new_transaction.png)

In this example user1, {port=1000} and user3, {port=3000} will be used.

From each's 'get_pub_key' we will get the public keys.

![user1 pub key](assets/user1_pub_key.png)
![user3 pub key](assets/user3_pub_key.png)

The definition will check the sender's wallet balance. 
If the requested amount is greater than it,
the transaction will be terminated.

    For example, initially the wallet will contain 50 coins.
    An attempt of sending 60 coins will be made.

![false example](assets/def_new_transaction_false_example.png)

As response, an error message will be sent,
informing that the balance is not enough.

![false example result](assets/def_new_transaction_false_example_results.png)
    
In contrast, this time we will set the amount to be 20.

![true example](assets/def_new_transaction_true_example.png)

This time, the transaction will be executed.

![true example result](assets/def_new_transaction_true_example_results.png)

###Step 5: @app method 'mine'

@para = None

After a new transaction is made,
'mine' is called to upload the record. 
After executing the 'mine' method, 
the transaction can be seen.
For each transaction, 0.5 coin is taken for fee.

![transaction record](assets/def_new_transaction_record.png)

The record can be verified in the 'full_chain'
    and 'get_balance' methods.

###Step 6: @app method 'get_node'

@para = None

Click the 'try it out' button, and then hit execute

![get node 'try it out](assets/def_get_node.png)
![get node 'execute'](assets/def_get_node_execute.png)

This will return the neighbor nodes stored in the table. 
Initially, no node will be contained.

@[empty get node](assets/def_get_node_empty.png)

###Step 7: @app method 'register'

@para = target

This definition takes in 1 parameter:
    
    target => node's ip address 
    For Windows: 127.0.0.1:{port}
    For MAC: 0.0.0:{port}

To store other nodes in the relationship table, 
execute the method.

![register node](assets/def_register_node.png)

Message will show the node have been added.

![register node result](assets/def_register_node_response.png)

###Step 8: @app method 'get_node'

Execute the definition. 
This time, port 3000 will be shown.

![get node result](assets/def_get_node_success.png)

###Step 9: @app method 'consensus'

@para = None

Click the 'try it out' button, and then hit execute.

![consensus 'try it out'](assets/def_consensus.png)
![consensus 'execute'](assets/def_consensus_execute.png)

It will check the validity.

![consensus check](assets/def_consensus_results.png)

####--Author Alex Yu