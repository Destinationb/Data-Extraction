# Data-Extraction
#School Project Repository

#DESCRIPTION: Automate data extraction from a PCAP file in Python 
#Use the pyshark library to provide a Python wrapper for the Wireshark network analysis tool

#Define the extract_packet_data function
#The function uses FileCapture from pyshark to open the PCAP file and iterate over each packet in the capture. 
#It then extracts relevant data such as the transport layer protocol, source and destination IP addresses, source and destination ports, and payload
#You can modify the code within the loop to process or store the extracted data according to your specific requirements

#Make sure to install the pyshark library before running the code. You can install it using the following command:

#pip install pyshark

import pyshark

def extract_packet_data(pcap_file):
    capture = pyshark.FileCapture(pcap_file)

    for packet in capture:
        protocol = packet.transport_layer
        source_ip = packet.ip.src
        destination_ip = packet.ip.dst
        source_port = packet[protocol].srcport
        destination_port = packet[protocol].dstport
        payload = packet[protocol].payload

        # Process or store the extracted data as needed
        print(f"Protocol: {protocol}")
        print(f"Source IP: {source_ip}")
        print(f"Destination IP: {destination_ip}")
        print(f"Source Port: {source_port}")
        print(f"Destination Port: {destination_port}")
        print(f"Payload: {payload}")
        print("-----------------------------------------")

    capture.close() 

#Specify the path to PCAP file
pcap_file_path = "path/to/your/pcap_file.pcap"

#call function to extract data from PCAP file
extract_packet_data(pcap_file_path)

#Replace "path/to/your/pcap_file.pcap" with the actual path to your PCAP file that you want to extract data from.
