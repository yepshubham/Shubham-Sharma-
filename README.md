import serial
import time

# Simulate LDR sensor readings
def get_ldr_readings(ldr1, ldr2):
    # Replace this with actual sensor readings
    return ldr1, ldr2

# Simulate servo control
def control_servo(servo_angle):
    # Replace this with actual servo control code
    print(f"Servo angle: {servo_angle}")

def main():
    # Initialize serial connection (if needed)
    # ser = serial.Serial('COM3', 9600, timeout=1)
    
    # Define error margin
    error_margin = 10
    
    # Initial servo angle
    servo_angle = 90
    
    while True:
        ldr1, ldr2 = get_ldr_readings(500, 600)  # Example readings
        
        # Calculate difference
        diff = abs(ldr1 - ldr2)
        
        if diff > error_margin:
            if ldr1 > ldr2:
                servo_angle -= 1
            else:
                servo_angle += 1
        
        # Ensure servo angle is within bounds
        servo_angle = max(0, min(servo_angle, 180))
        
        control_servo(servo_angle)
        
        time.sleep(0.1)

if __name__ == "__main__":
    main()
