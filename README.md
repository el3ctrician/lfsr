# LFSR - Linear Feedback Shift Register  

This repository contains a VHDL implementation of a Linear Feedback Shift Register (LFSR). LFSRs are commonly used for generating pseudo-random data in simulations, testing, and various digital designs.  

The design is an abstracted version inspired by the original implementation by Deepak Kumar Tala and Alexander H. Pham, available [here](http://www.asic-world.com/examples/vhdl/lfsr.html).  

## 🚀 Features  

- **Customizable Output Width**: Easily adjust the output width using the `width` generic parameter.  
- **Seed Initialization**: Set the initial seed value through the `seed` generic parameter.  
- **Enable and Reset**: Control the LFSR operation using enable (`CE`) and reset (`SCLR`) inputs.  
- **VHDL Compatible**: Designed for easy integration into your VHDL projects.  

## 📄 Usage  

1. **Add the Component**: Integrate the LFSR entity into your VHDL project.  
2. **Configure the Generics**:  
   - **Seed**: Set the initial seed value (integer).  
   - **Width**: Define the desired width of the LFSR output.  
3. **Connect the Ports**:  
   - **`cout`**: The pseudo-random output of the LFSR.  
   - **`CE`**: Enable signal to control counting.  
   - **`CLK`**: Clock input for synchronous operation.  
   - **`SCLR`**: Reset input to clear the LFSR.  
4. **Simulate**: Use the LFSR to generate pseudo-random data for testing or other applications.  

### Example Code Snippet  

Here’s an example of how to instantiate the LFSR entity in your VHDL design:  

```vhdl  
library ieee;  
use ieee.std_logic_1164.all;  

entity top_level is  
end entity;  

architecture behavior of top_level is  
  signal clk   : std_logic;  
  signal reset : std_logic;  
  signal enable: std_logic;  
  signal lfsr_out: std_logic_vector(7 downto 0);  

begin  

  lfsr_inst: entity work.lfsr  
    generic map (  
      seed  => 42,    -- Initial seed value  
      width => 8      -- Output width  
    )  
    port map (  
      cout   => lfsr_out,  
      CE     => enable,  
      CLK    => clk,  
      SCLR   => reset  
    );  

end architecture;  
```  

## 💡 Applications  

- Test data generation for simulation environments.  
- Pseudo-random sequence generation for hardware testing.  
- Scrambling and simple encryption purposes.  

## 📜 License  

This code is released under the GNU General Public License v3.0. You can find the full license text [here](https://www.gnu.org/licenses/gpl-3.0.en.html).  

## 🤝 Credits  

- Original inspiration: Deepak Kumar Tala and Alexander H. Pham ([ASIC-World](http://www.asic-world.com/examples/vhdl/lfsr.html))  
