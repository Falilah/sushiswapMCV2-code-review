SUSHI MASTERCHEFV2 CONTRACT REVIEW
@nOTICE THE CONTRACT

lp=Liquidity pool

UserInfo: This is a struct use to keep information of users:

        amount: Total mount LP tokens the user has provided.
        rewardDebt keeps track of how much the user is owed or has been credited already

PoolInfo is a struct that keeps information on LP position

        accSushiPerShare: Accumulated SUSHIs per share, times 1e12.

        lastRewardBlock: Last block number that SUSHIs distribution occurs.

        allocPoint: How many allocation points assigned to this pool

MasterChef address of MasterChef contract

sushi address of sushi contract

MASTER_PID pool: the id of dummy Token on MasterChef V1

totalAllocPoint Total allocation points. Must be the sum of all allocation points in all pools.

The following arrays should be accessed by the same index pid

        PoolInfo[] public poolInfo: Array of PoolInfo Struct

        IERC20[] public lpToken: Array of address of token in the pool

        IRewarder[] public rewarder: array of addressses of rewarder

CONSTRUCTOR: THE ADDRESS OF ALL THE CONTRACT MASTERCHEFV2 will interact with is being set.

/****************\*****************

#init function.

@notice Deposits a dummy token to `MASTER_CHEF` MCV1. This is required because MCV1 holds the minting rights for SUSHI.
Any balance of transaction sender in `dummyToken` is transferred.
The allocation point for the pool on MCV1 is the total allocation point for all pools that receive double incentives.
@param dummyToken The address of the ERC-20 token to deposit into MCV1.

Access the balance the user has in the token address he has inputed and made safeTransferFrom from the token contract to masterchefv2.
approve masterchefv1 to spend the money
the deposit function of masterchef v1 was interaacted with to get the money in the pool

        /*******
        the token address could be any erc20 token as long as the caller of the function has the token ***?

        /**** safeTransferFrom function is the function that allow token to be transferred from the token contract to masterchefV2 contract after it must have been approved by the caller of the init function.

        /***** the deposit function called from the masterchefv1 contract which helps to calculate the amount of sushi token to be transfer to the msg.sender, it update the pool ID, it calculate the reward the caller is entitle to also.
        *****************************/

/********************\*\*\*********************

#Add function

/// @notice Add a new LP to the pool. Can only be called by the owner.
DO NOT add the same LP token more than once. Rewards will be messed up if you do.
@param allocPoint AP of the new pool.
@param \_lpToken Address of the LP ERC-20 token.
@param \_rewarder Address of the rewarder delegate.

function add which can only be called by the owner in order to add new liquidity pool to the pool.
This was done in the following ways:

        The owner input the allocationpoint, the token contract address, and the rewarder contract address.

        Assigned a block.number to a local variable.

        Added the allocationPoint to the TotalAllocationPoint
        pushed token address and rewarder address to their respective Arrays.

        updated the structValue and push them to an Array of struct.

**************\***************/

/************\*************

#SET FUNCTION.

        @notice Update the given pool's SUSHI allocation point and `IRewarder` contract. Can only be called by the owner.
        @param _pid The index of the pool. See `poolInfo`.
        @param _allocPoint New AP of the pool.
        @param _rewarder Address of the rewarder delegate.
        @param overwrite True if _rewarder should be `set`. Otherwise `_rewarder` is ignored.

MORE DETAILS:  
set function update the pool's sushi allocation and Irewarder contract and can only be called by the owner

since the function is to update the pool
previous allocationPoint was removed and the new allocationpoint was added to totalAllocationPoint

allocationPoint was also reassigned in the PoolInfo struct using a struct pointer.

if overwrite is true rewarder will be set else it won't.

************\*\*\*\*************/

/************\*\*************

#SETMIGRATOR FUNCTION

        @notice Set the `migrator` contract. Can only be called by the owner.
        @param _migrator The contract address to set.

        in this function migrator was set
        migrator is a contract  that deals

******************\*\*\*******************/

/**************\*\***************
#migrate

        @notice Migrate LP token to another LP contract through the `migrator` contract.
        @param _pid The index of the pool. See `poolInfo`.

More explanation:

this function checked that migrator has been set,
Assigned the token from the array to a local variable and also the balance mcv2 contract has to a local variable also.
MCV2 approved the migrator to spend it's token
then the migrate function was called from the migratetor contract.

        the migrator contract interact with uniswapV2pair which is the contract incharge of creating new contract for each pair of token using Create2.

******************\*******************/

/**********\*\***********
#pendingSushi

        @notice View function to see pending SUSHI on frontend.
        @param _pid The index of the pool. See `poolInfo`.
        @param _user Address of user.
        @return pending SUSHI reward for a given user.

the pending sussshi as display above get the pending sushi token:

        after inputing the ID of that particular token and the address of given user in that pool, using the information provided to get the necessary information from the struct.
        time is calculated to calculate the reward the user is entitle to from the pool.
        all these above information is the used to calculating the amount pending for that users.

**************\*\***************/
/**********\***********

#massUpdatePools

        @notice Update reward variables for all pools. Be careful of gas spending!
        @param pids Pool IDs of all to be updated. Make sure to update all active pools.

this function basically update the pools in mass as the name implies which called another function named updatePool while looping through each Id in the arrays
************\*\*\*\*************/
/**********\*\*\*\***********

#sushiPerBlock

        @notice Calculates and returns the `amount` of SUSHI per block.

**************\*\***************/

/************\*************

#updatePool

        @notice Update reward variables of the given pool.
        @param pid The index of the pool. See `poolInfo`.
        @return pool Returns the pool that was updated.

**********\*\***********/
/**********\*\*\*\***********

#deposit

        @notice Deposit LP tokens to MCV2 for SUSHI allocation.
        @param pid The index of the pool. See `poolInfo`.
        @param amount LP token amount to deposit.
        @param to The receiver of `amount` deposit benefit.

************\*************/
/**************\*\*\***************

#withdraw

        @notice Withdraw LP tokens from MCV2.
        @param pid The index of the pool. See `poolInfo`.
        @param amount LP token amount to withdraw.
        @param to Receiver of the LP tokens.

**********************\***********************/

/******************\*\*******************

#harvest

        @notice Harvest proceeds for transaction sender to `to`.
        @param pid The index of the pool. See `poolInfo`.
        @param to Receiver of SUSHI rewards.

******************\*******************/
/****************\*\*****************

#withdrawAndHarvest

harvest proceeds for transaction sender to `to`.
@param pid The index of the pool. See `poolInfo`.
@param amount LP token amount to withdraw.
@param to Receiver of the LP tokens and SUSHI rewards.

********************\*\*\*********************/
/********************\*********************

#harvestFromMasterChef

        @notice Harvests SUSHI from `MASTER_CHEF` MCV1 and pool `MASTER_PID` to this MCV2 contract.
        function

**********\***********/
/**********\*\*\*\***********
#emergencyWithdraw

        @notice Withdraw without caring about rewards. EMERGENCY ONLY.
        @param pid The index of the pool. See `poolInfo`.
        @param to Receiver of the LP tokens.

************\*\*************/
