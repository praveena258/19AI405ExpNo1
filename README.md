<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: PRAVEENA D</h3>
<h3>Register Number/Staff Id: 212224040248</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

 <h3>program</h3>
 
```
python
import random

# Define the environment: 2 rooms with patients
rooms = {
    "Room 1": {"temperature": random.uniform(97, 102), "treated": False},
    "Room 2": {"temperature": random.uniform(97, 102), "treated": False}
}

# Agent performance
performance = 0

# Medicine prescribing agent
class MedicineAgent:
    def __init__(self):
        self.current_room = "Room 1"

    # Sensor: check patient's temperature
    def check_patient(self, room):
        temp = rooms[room]["temperature"]
        print(f"{room} patient temperature: {temp:.2f}")
        return temp

    # Actuator: prescribe medicine if patient is unhealthy
    def treat_patient(self, room):
        global performance
        if rooms[room]["temperature"] > 98.5 and not rooms[room]["treated"]:
            print(f"Treating patient in {room}...")
            rooms[room]["treated"] = True
            performance += 10  # increase performance for treating
        else:
            print(f"No treatment needed in {room}.")

    # Move agent to another room
    def move_to(self, room):
        global performance
        if self.current_room != room:
            print(f"Moving from {self.current_room} to {room}...")
            self.current_room = room
            performance -= 1  # movement reduces performance

agent = MedicineAgent()

# Agent performs actions in both rooms
for room in rooms:
    temp = agent.check_patient(room)
    agent.treat_patient(room)
    if room == "Room 1":
        agent.move_to("Room 2")  # move to next room

print("\nFinal Performance:", performance)
print("Room Status:", rooms)

```
<h3>OUTPUT</h3>
<img width="1469" height="340" alt="image" src="https://github.com/user-attachments/assets/1cc72988-e960-4218-a943-863cd1329cbc" />

