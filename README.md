# auto-switch-electrical
import time
import random  # For simulation purposes

class AutomaticSwitch:
    def __init__(self):
        self.is_on = False
        self.last_check_time = time.time()
        self.check_interval = 60  # Check every 60 seconds for example
        
    def simulate_sensor_reading(self):
        # Simulate light sensor or time-based condition
        return random.randint(0, 100)  # 0-100 range for light level or any condition

    def check_conditions(self):
        # This method should contain the logic for when to switch on/off
        current_time = time.time()
        if current_time - self.last_check_time >= self.check_interval:
            self.last_check_time = current_time
            sensor_reading = self.simulate_sensor_reading()
            if sensor_reading < 20:  # Assuming light level below 20% is considered dark
                if not self.is_on:
                    self.turn_on()
            else:
                if self.is_on:
                    self.turn_off()

    def turn_on(self):
        self.is_on = True
        print("Switching ON at", time.strftime("%H:%M:%S", time.localtime()))

    def turn_off(self):
        self.is_on = False
        print("Switching OFF at", time.strftime("%H:%M:%S", time.localtime()))

    def run(self):
        while True:
            self.check_conditions()
            time.sleep(1)  # Check conditions every second for simulation

if __name__ == "__main__":
    auto_switch = AutomaticSwitch()
    auto_switch.run()
