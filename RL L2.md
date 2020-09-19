### Intro
Markov Decision Process describes an environment
1. environment is fully observable
2. current state ---> future state
3. All RL problem could be transformed to MDPs
partially observable
cts MDPs

### from MP to MRP to MDP 
*chain: add reward and action*
#### Markov Property
The future is independent of the past given the present
S_t is Markov if only if 
```math
P[S_{t+1} | S_t ] = P[S_t+1 | S_1, S_2,....S_t]
```
```math
S_t could orient the future
```
#### Markov Process (Markov Chain)
<S,P>
S finite set of states
P state transition probability matrix：矩阵描述所有状态转换概率
```math
P =
\begin{bmatrix}
 P_11 & ... & P_1n\\
 .      & .  & .    \\
 P_n1 &.   & P_nn    
\end{bmatrix}
```
State Transition Matrix:描述从当前状态s到s’状态的概率
```math
P_ss' = P[S_{t+1} = s' | S_t= s]
```
#### Markov Reward Process
<S,P,R,γ>
S finite set of states
P state transition probability matrix
R reward function :从当前状态离开获得reward
```math
R_s = E[R_t+1 | S_t = s]
```
γ discount factor


**思路：从【一个sample（一条路径，S1,S2,S3）】到【S1】思考**
**G_t** **return: total discounted reward from time step t**
for a finite set of state (a chain of state) = a sample 
```math
G_t = R_{t+1} + γR_{t+2} ... = \sum_{k = 0} \gamma^k R_{t+k+1}
```
```math
γ \in [0,1]
```

γ=0只关注当下奖励myopic evaluation
γ=1远视
γ discount factor 
1. human/animal prefer immediate R_t is 1
2. uncertainty even though it is a set of state
3. math : avoid infinite

**v(s)** **state value function: evaluate how well is this state?**
从当下状态s出发under s，求G_t 的conditional期望（由于随机性）
```math
v(s) = E[G_t | S_t = s]
```
经过推导
期望打开后变成 = 概率* value function 求和
v（s) = Immediate Reward R_t + discounted value γv(S_t+1)
```math
v(s) = R_s + γ \sum_{s' \in S}P_{ss'}v(s')
```
* 理解：为了衡量当前状态好不好，通过计算当前状态的reward与未来一系列状态的value function直到termination

* Bellman Equation：动态规划方程
思路：将贝尔曼方程--> Linear equation --> matrix
解matrix即可

* extension：
Dynamic programming
Monte-Carlo evaluation

### Markov Decision Process
##### definition
<S,A,P,R,γ>
P transition probability matrix中 P is probability under St = s, At=a
A finite set of states
R reward function . Similarly under condition St = s, At= a

**Policy pi** 
Π: distribution over actions given states 
```math
pi(a|s) =P[A_t = a|S_t = s]
```
在s状态下，有a1，a2action，a1 action的概率是pi(a1|s)
##### value function
**vΠ(s) state value function**
**qΠ(a,s) action value function** **in MDP evaluate how well is this action**

##### find the best solution
**intuition** 
get best reward -> get highest reward every step -> get highest value function every state -> how to find the pi to get this highest value function
**there may be not only one best policy but they orient the value function to the same value**
非线性方程 no closed solution



