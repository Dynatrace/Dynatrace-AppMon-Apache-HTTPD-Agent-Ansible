# Dynatrace-Apache-HTTPServer-Agent-Ansible

An [Ansible](http://www.ansible.com) role for automated deployments of the [Dynatrace](http://www.bit.ly/dttrial) Agent for the Apache HTTP Server.

This role makes the Agent available to the Apache HTTP Server by injecting a *LoadModule* directive into the HTTP Server's config file. Optionally, the HTTP Server's init.d (LSB) script is manipulated such that the Apache HTTP Server service is started only after the Dynatrace Web Server Agent service has started.

**Note**: You have to restart the Apache HTTP Server after placing the agent.

**Note**: Currently, we support only Linux hosts, support for installing Windows hosts is in the making.

## Download

The role is available via:

- [Ansible Galaxy](https://galaxy.ansible.com/list#/roles/2681)
- [GitHub](https://github.com/Dynatrace/Dynatrace-Apache-HTTPServer-Agent-Ansible)

## Requirements

This roles requires an installation of the Dynatrace WebServer Agent, which is provided by the following roles:

- [Dynatrace-WebServer-Agent](https://galaxy.ansible.com/list#/roles/2625)
- [Dynatrace-Server](https://galaxy.ansible.com/list#/roles/2623)

## Role Variables

As defined in ```defaults/main.yml```:

| Name                                                    | Default                                  | Description |
|---------------------------------------------------------|------------------------------------------|-------------|
| *dynatrace_apache_agent_linux_agent_path*               | /opt/dynatrace/agent/lib64/libdtagent.so | The path to the Agent library. |
| *dynatrace_apache_agent_linux_apache_config_path*       | /etc/apache2/apache2.conf                | The path to the Apache HTTP Server's config file. |
| *dynatrace_apache_agent_linux_apache_initd_script_path* | /etc/init.d/apache2                      | The path to the Apache HTTP Server's init.d script. |
| *dynatrace_apache_agent_do_patch_apache_initd_script*   | yes                                      | Whether the init.d script shall be patched so that the Apache HTTP Server service is started only after the Dynatrace Web Server Agent service has started, or not.
| *dynatrace_apache_agent_state*                          | present                                  | Whether the Agent shall be ```present``` or ```absent```. |

## Example Playbook

	- hosts: all
	  roles:
	    - { role: Dynatrace-WebServer-Agent }
	    - { role: Dynatrace-Apache-HTTPServer-Agent }

## Additional Resources

- [Slide Deck: Automated Deployments](http://slideshare.net/MartinEtmajer/automated-deployments-slide-share)
- [Slide Deck: Introduction to Automated Deployments with Ansible](http://www.slideshare.net/MartinEtmajer/introduction-to-automated-deployments-with-ansible)

## Questions?

Feel free to post your questions on the Dynatrace Community's [Continuous Delivery Forum](https://community.dynatrace.com/community/pages/viewpage.action?pageId=46628921).

## License

Licensed under the MIT License. See the LICENSE file for details.
[![analytics](https://www.google-analytics.com/collect?v=1&t=pageview&_s=1&dl=https%3A%2F%2Fgithub.com%2FdynaTrace&dp=%2FDynatrace-Apache-HTTPServer-Agent-Ansible&dt=Dynatrace-Apache-HTTPServer-Agent-Ansible&_u=Dynatrace~&cid=github.com%2FdynaTrace&tid=UA-54510554-5&aip=1)]()