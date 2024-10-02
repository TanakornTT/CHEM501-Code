import numpy as np
import serial
import os
import pandas as pd

nicla = serial.Serial(port='/dev/cu.usbmodemAE4E41EF2', baudrate=115200, timeout=.1)

nicla.flush()
nicla.reset_input_buffer()

while True:
    try:
        num_datasets = int(input("How many datasets would you like to save? "))
        if num_datasets > 0:
            break
        else:
            print("Please enter a positive integer.")
    except ValueError:
        print("Invalid input. Please enter a valid number.")

indices = []
for i in range(num_datasets):
    while True:
        try:
            index = int(input(f"Enter the line number for dataset {i+1}: "))
            if index > 0:
                indices.append(index)
                break
            else:
                print("Please enter a positive integer.")
        except ValueError:
            print("Invalid input. Please enter a valid number.")

