import streamlit as st
import socket
from datetime import datetime

st.title("Port Scanner")

# Function to perform port scanning
def port_scan(target):
    try:
        ip = socket.gethostbyname(target)

        st.write("-" * 50)
        st.write("Scanning target:", ip)
        st.write("Time started:", datetime.now())
        st.write("-" * 50)

        open_ports = []

        for port in range(1, 65635):
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.settimeout(1)
            result = sock.connect_ex((ip, port))
            if result == 0:
                open_ports.append(port)
            sock.close()

        if open_ports:
            st.write("Open ports:")
            st.write(open_ports)
        else:
            st.write("No open ports found.")

    except socket.gaierror:
        st.write("Hostname could not be resolved.")

    except socket.error:
        st.write("Could not connect to the server.")

# Get user input for the target
target = st.text_input("Enter the target IP address or hostname:")

# Trigger the port scanning when the user clicks the button
if st.button("Scan Ports"):
    port_scan(target)
