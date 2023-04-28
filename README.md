# Digital-Logic-Design-2021-2022
---
author:
- Beatrice Insalata - *10708628*
- Teka Kimbi Ntimanputu - *10673197*

---
# Digital Logic Design Project 2021-2022
Final Mark : 30/30


# Convolutional Codification and Project Introduction
Convolutional encoding is a type of encoding used for Forward Error Correction (FEC) in telecommunications systems based on unidirectional channels.

Through convolutional encoding, a convolutional code is generated, which transforms each word $P_1$ into a word $P_2$. Let $l_1 = length (P_1)$ and $l_2 = length (P_2)$ be defined, the ratio $l_1/l_2$ is defined as  *the convolutional encoder's transmission rate*, with $l_2 \geq l_1$.

Furthermore, the transformation is a function of the last $k$ input bits, where k is the code's *constraint length*.

The purpose of the project is to implement a hardware component, using the VHDL hardware specification language, capable of interfacing with a RAM memory and applying a convolutional encoding with $rate = \frac{1}{2}$ and $k = 3$.

## Project Requirements

The project interface, the memory specification to interface with, and a time limitation that requires the hardware module to correctly compute with clock periods of at least $clockPeriod_{req} = 100ns$ are provided.

Below is the interface of the module and the interface of the memory.

### Interface

``` vhdl
entity project_reti_logiche is
    port (
        i_clk : in std_logic;
        i_rst : in std_logic;
        i_start : in std_logic;
        i_data : in std_logic_vector(7 downto 0);
        o_address : out std_logic_vector(15 downto 0);
        o_done : out std_logic;
        o_en : out std_logic;
        o_we : out std_logic;
        o_data : out std_logic_vector (7 downto 0)
    );
end project_reti_logiche;
```

### Memory Interface

``` vhdl
entity rams_sp_wf is
    port(
        clk : in std_logic;
        we : in std_logic;
        en : in std_logic;
        addr : in std_logic_vector(15 downto 0);
        di : in std_logic_vector(7 downto 0);
        do : out std_logic_vector(7 downto 0)
    );
end rams_sp_wf;
```

The following link to Vivado's *User Guide* provides further details:
<https://www.xilinx.com/support/documentation/sw_manuals/xilinx2017_3/ug901-vivado-synthesis.pdf>

# Architettura, approccio e scelte implementative

We decided to follow a *FSM* approach in the implementation of our component module. The complete project description, along with performance indicators and tests, are found in the report folder.
