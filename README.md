Download Link: https://assignmentchef.com/product/solved-ece-321-assignment-4-petri-net-pn-model
<br>
This question asks you to provide the Petri Net (PN) model of the traffic light system that was elicited during the laboratories and which is shown on the right.

Your solution should include:

<ol>

 <li> A <strong>graph</strong> representing your model, i.e., a screenshot showing the initial marking that represents the <strong>Default</strong> state included in the PDF <strong>AND</strong> the model as <strong>xml</strong> file submitted on eClass before the deadline. The xml file <strong>must be created with PIPE 4.3.0</strong> that can be downloaded from</li>

</ol>

<a href="https://sourceforge.net/projects/pipe2/files/PIPEv4/PIPEv4.3.0/">https://sourceforge.net/projects/pipe2/files/PIPEv4/PIPEv4.3.0/ </a>Try to make your model as neat as possible.

<ol start="2">

 <li> A <strong>description of all transitions</strong> used in the graph

  <ol>

   <li>List all transitions and describe what each of them does</li>

  </ol></li>

 <li> The <strong>answer</strong> to the following three questions

  <ol>

   <li>Is your model conservative? Explain why.</li>

   <li>Can we have a deadlock in your model?</li>

   <li>Can we have a starvation in your model? If yes then show an example corresponding cycle and list the transitions that will starve. Discuss if this starvation could happen in the actual live traffic lights system, and if yes, explain in words how to prevent it.</li>

  </ol></li>

</ol>

Your system will use the following definition of states to derive the PN model:

<strong>Inputs</strong><strong> 1 2 3 G1 G3 P1 P2 P3 M C T1 T2 B3* S2** </strong><strong>Valid states for given</strong> G, G, G, G, G, G,

<strong>input</strong> R,          R,      R,     On,     On,                                      On,      D,      On,     On,     On,      On,

<strong>System states                                        </strong>Off FR FR Off Off OffR, <strong> </strong>OffR, <strong> </strong>Off<sup>R, </sup><strong> </strong>Off<strong>               </strong>N<strong>         </strong>Off Off        Off       Off

Default                                              G       R       R      Off     Off      R        G        R       Off       D       On     Off      Off       Off

DefaultB3                                         G       R       R      Off     Off      R        G        R       Off       D       On     Off      On       Off

DefaultS2                                          G       R       R      Off     Off      R        G        R       Off       D       On     Off      Off       On

DefaultB3S2       G             R             R             Off          Off          R             G             R             Off          D             On          Off          On               On GreenP3          G             R             R             Off          Off          R             G             G             Off          D             Off       On               On          Off GreenP3S2    G             R             R             Off          Off          R             G             G             Off          D             Off           On          On          On GreenG1         R             R             R             On          Off          G             R             R             Off          D               Off       On          Off          Off GreenG1S2    R             R             R             On          Off          G             R             R             Off               D             Off       On          Off          On Green3            R             R             G             Off          On          R             R             R               Off          D             Off       On          Off          Off Green3S2       R             R             G             Off          On          R             R               R             Off          D             Off       On          Off          On

Green2and3                                      R        G       G      Off     Off      R        R        R       Off       D       Off    On      Off       Off

Emergency                                      Off     FR     FR     Off     Off     Off     Off     Off     On     D/N     Off     Off      Off       Off

Night                                                Off     FR     FR     Off     Off     Off     Off     Off     Off       N       Off     Off      Off       Off




M denotes malfunction flag; C clock (day vs. night); T1 and T2 are timers

* “B3 = On” only if B3 was pressed before leaving the Default state

** “S2 = On” only if S2 was active before leaving the Default state

The transitions between the states are described by the following transition function table:

<strong>IMPORTANT NOTES</strong>

<ul>

 <li>The Petri Net model has to follow the below assumptions</li>

</ul>

◦ <strong>Places represent the objects, not the states of the entire system</strong> (in contrast to the Finite State Machine model), e.g. you will have a place for traffic lights 1, traffic lights 2, etc. See below for the list of places that are in the model.

◦ <strong>Each transition is enabled based on its input places</strong>

&#x25aa; You may need to define multiple (duplicate) transitions that will model the same physical input that changes system state, e.g. for the timer in the default state, but which will be enabled in different states

◦ Inputs from the two sensors (B3 and S2) are considered/acknowledged <strong>only</strong> in the Default state; columns B3 and S2 represent the state of the inputs as read in the Default state. If they were not triggered in Default but became triggered in a subsequent state, then they are not going to be acted upon until after the Default states. It is possible that both inputs, one of the inputs, or none of the inputs are triggered. They are activated (set to On) one at the time, i.e., never at the same time. At the time when Timer1 (T1) expires, the possible configurations are that both inputs, one of the inputs, or none of the inputs are triggered. ◦ The switch to the Night state is possible <strong>only</strong> in the “Default” states (including Default, DefaultB3, DefaultS2 and DefaultB3S2). Your model has to <strong>reset the values in the B3 and S2 columns</strong> (set them to Off) when you transition out of the Default state, i.e., when the Night time input is read.

◦ To simplify the model, the Emergency state is disregarded (shadowed cells in the tables above should be ignored). Other than that, the Petri Net model must represent the complete behavior of the system

◦ It is not allowed to modify the above physical representation of the system states (colors of the lights, setup of the timers, malfunction input, etc.)

◦ Remember to list any additional assumptions about your model, if you make any

◦ <strong>Use the input and input state abbreviations, as defined in the above table, in your model. Renaming will result in deductions.</strong>

◦ <strong>Use PIPE 4.3.0</strong>

◦ <strong>Remember that Petri Nets are nondeterministic</strong>

&#x25aa; They fire one of the enabled transitions non-deterministically

&#x25aa; You do not have the control of which one

&#x25aa; One of the enabled transitions is selected randomly, which means that you need to simulate and verify all possibilities