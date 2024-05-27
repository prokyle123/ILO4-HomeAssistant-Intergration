# HP iLO Sensor Integration with Home Assistant

## 🌟 Overview

This project integrates HP iLO (Integrated Lights-Out) sensors with Home Assistant to monitor and gather vital statistics from an HP server. Using Home Assistant, the sensor data is fetched and displayed, providing real-time information about the server's health and status.

## 🔥 Features

- **Fan Status Monitoring**: Keep track of the status of the server fans.
- **Memory Status Monitoring**: Monitor the status of the server's memory.
- **Network Status Monitoring**: Check the network status of the server.
- **Processor Status Monitoring**: Get real-time updates on the processor status.
- **Storage Status Monitoring**: Monitor the storage health status.
- **Temperature Status Monitoring**: Check the temperature status of the server.
- **Memory Size Monitoring**: Monitor the total memory size of CPU 1.
- **NIC iLO Status Monitoring**: Check the status of the iLO NIC.
- **Power Consumption Monitoring**: Monitor the current power consumption in watts.
- **Inlet Temperature Monitoring**: Measure the inlet temperature in Fahrenheit.
- **Fan Speed Monitoring**: Monitor the speed of each fan in percentage.
- **CPU Temperature Monitoring**: Get the temperatures of CPU 1 and CPU 2 in Fahrenheit.
- **Temperature Monitoring for Specific Components**: Monitor temperatures for HD Controller, Exhaust, and Chipset.

## 🛠️ Hardware Requirements

- **HP Server with iLO**: Ensure that the server has iLO configured and accessible.

## 🖥️ Software Requirements

- **Home Assistant**: An open-source platform for smart home automation.
- **HP iLO Integration**: Make sure the HP iLO integration is enabled in Home Assistant.

## 🔌 Hardware Setup

This integration primarily involves network communication with the HP iLO interface. Ensure your Home Assistant instance has network access to the HP iLO interface.

## 🚀 Getting Started

1. **Add the HP iLO Integration**: Add the HP iLO integration to your Home Assistant setup by including the following in your `configuration.yaml` file:

   ```yaml
   sensor:
     - platform: hp_ilo
       host: 192.168.12.190
       username: USE YOURS
       password: USE YOURS
       scan_interval: 120

       monitored_variables:
         - name: fan_status
           sensor_type: server_health
           value_template: "{{ ilo_data.health_at_a_glance['fans']['status'] }}"

         - name: memory_status
           sensor_type: server_health
           value_template: "{{ ilo_data.health_at_a_glance['memory']['status'] }}"

         - name: network_status
           sensor_type: server_health
           value_template: "{{ ilo_data.health_at_a_glance['network']['status'] }}"

         - name: processor_status
           sensor_type: server_health
           value_template: "{{ ilo_data.health_at_a_glance['processor']['status'] }}"

         - name: storage_status
           sensor_type: server_health
           value_template: "{{ ilo_data.health_at_a_glance['storage']['status'] }}"

         - name: temperature_status
           sensor_type: server_health
           value_template: "{{ ilo_data.health_at_a_glance['temperature']['status'] }}"

         - name: memory_cpu1_size
           sensor_type: server_health
           value_template: "{{ ilo_data.memory['memory_details_summary']['cpu_1']['total_memory_size'] }}"

         - name: nic_ilo_status
           sensor_type: server_health
           value_template: "{{ ilo_data.nic_information['iLO iLO Dedicated Network Port']['status'] }}"

         - name: Watts
           sensor_type: server_health
           value_template: "{{ ilo_data.power_supply_summary['present_power_reading'] }}"

         - name: Inlet Temp
           sensor_type: server_health
           unit_of_measurement: '°F'
           value_template: '{{ (ilo_data.temperature["01-Front Ambient"].currentreading[0]*9/5) + 32 }}'

         - name: Fan1
           sensor_type: server_health
           unit_of_measurement: '%'
           value_template: '{{ ilo_data.fans["Fan 1"].speed[0] }}'

         - name: Fan2
           sensor_type: server_health
           unit_of_measurement: '%'
           value_template: '{{ ilo_data.fans["Fan 2"].speed[0] }}'

         - name: Fan3
           sensor_type: server_health
           unit_of_measurement: '%'
           value_template: '{{ ilo_data.fans["Fan 3"].speed[0] }}'

         - name: Fan4
           sensor_type: server_health
           unit_of_measurement: '%'
           value_template: '{{ ilo_data.fans["Fan 4"].speed[0] }}'

         - name: Fan5
           sensor_type: server_health
           unit_of_measurement: '%'
           value_template: '{{ ilo_data.fans["Fan 5"].speed[0] }}'

         - name: Fan6
           sensor_type: server_health
           unit_of_measurement: '%'
           value_template: '{{ ilo_data.fans["Fan 6"].speed[0] }}'

         - name: cpu1temp
           sensor_type: server_health
           unit_of_measurement: '°F'
           value_template: '{{ (ilo_data.temperature["02-CPU 1"].currentreading[0]*9/5) + 32 }}'

         - name: cpu2temp
           sensor_type: server_health
           unit_of_measurement: '°F'
           value_template: '{{ (ilo_data.temperature["03-CPU 2"].currentreading[0]*9/5) + 32 }}'

         - name: HDController
           sensor_type: server_health
           unit_of_measurement: '°F'
           value_template: '{{ (ilo_data.temperature["25-HD Controller"].currentreading[0]*9/5) + 32 }}'

         - name: ExhastTemp
           sensor_type: server_health
           unit_of_measurement: '°F'
           value_template: '{{ (ilo_data.temperature["50-Sys Exhaust"].currentreading[0]*9/5) + 32 }}'

         - name: Chipset
           sensor_type: server_health
           unit_of_measurement: '°F'
           value_template: '{{ (ilo_data.temperature["13-Chipset"].currentreading[0]*9/5) + 32 }}'
   ```

2. **Restart Home Assistant**: After editing the configuration file, restart Home Assistant to apply the changes.

3. **Monitor the Data**: Once Home Assistant is running, you can view the data from the iLO sensors on the Home Assistant dashboard. The sensors will provide real-time updates on various server parameters.

## 📚 Documentation

For more detailed information on Home Assistant configurations and integrations, refer to the [Home Assistant Documentation](https://www.home-assistant.io/).

## 🤝 Contributing

We welcome contributions to this project! Feel free to open issues or submit pull requests on GitHub. Together, we can improve and expand the capabilities of the HP iLO Sensor Integration Project.

## 📧 Contact

If you have any questions or need further assistance, please open an issue on GitHub or contact me at prokyle123@gmail.com.

---

