We have to run the picorv32a design synthesis using openLANE flow and generate design statistics and synthesis reports.

To invoke openLANE flow and perform the synthesis we use the following commands inside openlane folder in terminal:

**To invoke openLANE flow**
```bash
docker
```
To run the flow in interactive (step-by-step) mode
```
./flow.tcl -interactive
```
Import required packages
```
% package require openlane 0.9
```
To prepare the picorv32a design and setup necessary folders and files for synthesis
```
% prep -design picorv32a
```
<img width="733" height="486" alt="Screenshot 2025-07-27 054942" src="https://github.com/user-attachments/assets/7df1c68f-b29f-4334-a69f-d1a3dbd3bd51" />

<img width="600" height="476" alt="Screenshot 2025-07-27 062407" src="https://github.com/user-attachments/assets/ff335fa3-4c89-41da-bf5d-7b1718988541" />

<img width="608" height="461" alt="Screenshot 2025-07-27 062448" src="https://github.com/user-attachments/assets/48a9ab9e-9f27-475a-ba60-d1e7dfebb9f7" />

2. Calculate the flop ratio.
Screenshots of synthesis statistics report file with required values highlighted

<img width="391" height="442" alt="Screenshot 2025-07-27 055913" src="https://github.com/user-attachments/assets/51026831-1d7e-4575-8a49-75feeff5d3da" />

<img width="375" height="201" alt="Screenshot 2025-07-27 055956" src="https://github.com/user-attachments/assets/df3d9620-ac31-4824-b8a1-546dfb857053" />

Calculation of Flop Ratio and DFF % from synthesis statistics report file

$$Flop\ Ratio = \frac{1613}{14876} = 0.108429685$$
$$Percentage\ of\ DFF's = 0.108429685 \times 100 = 10.84296854%\ \%$$

1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
Commands to invoke the OpenLANE flow and perform floorplan
```
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
```
```
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Now we can run floorplan
run_floorplan
```


