+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|              Name | Instance | Type |      Values | Default |                                                                                                                         Documentation |
+===================+==========+======+=============+=========+=======================================================================================================================================+
|         ARITH_SEL |      0-9 |  Mux | - adder     |     lut |                                                                      Select whether the data input of the FF is the LUTs or the adder |
|                   |          |      | - lut       |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          BCLK_SEL |      0-9 |  Mux | - off       |     off |                                                                                          Select the clock input to the two bottom FFs |
|                   |          |      | - clk0      |         |                                                                                                                                       |
|                   |          |      | - clk1      |         |                                                                                                                                       |
|                   |          |      | - clk2      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          BCLR_SEL |      0-9 |  Num | - 0-1       |       0 |                                                                                           Select the aclr input to the two bottom FFs |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|             BDFF0 |      0-9 |  Mux | - reg       |     reg |                                                                                             Select between LUT and FF for that output |
|                   |          |      | - nlut      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|             BDFF1 |      0-9 |  Mux | - reg       |     reg |                                                                                             Select between LUT and FF for that output |
|                   |          |      | - nlut      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|            BDFF1L |      0-9 |  Mux | - reg       |     reg |                                                                                             Select between LUT and FF for that output |
|                   |          |      | - nlut      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           BEF_SEL |      0-9 |  Mux | - e         |       e |                                                                      Select which input goes to the sdata input of the two bottom FFs |
|                   |          |      | - f         |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           BPKREG0 |      0-9 | Bool |         t/f |       f |                                                                     Force the top FF of the bottom half to get its input from tef_sel |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           BPKREG1 |      0-9 | Bool |         t/f |       f |                                                                  Force the bottom FF of the bottom half to get its input from tef_sel |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         BSCLR_DIS |      0-9 | Bool |         t/f |       f |                                                                                                Disable sync clear for the bottom half |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         BSLOAD_EN |      0-9 | Bool |         t/f |       f |                                                                     Select whether to enable the sync load line of the two bottom FFs |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|    B_FEEDBACK_SEL |      0-9 |  Num | - 0-1       |       0 |                                                                              Select which of the FFs goes to the bottom feedback line |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          LUT_MASK |      0-9 |  Ram |     64 bits |       0 |                                                              LUT values, A has bits 0-15, B 16-23, C 24-31, D 32-47, E 48-55. F 56-63 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|              MODE |      0-9 |  Mux | - l5        |      l6 |                                                                                                         Connectivity mode of the cell |
|                   |          |      | - l5_ft     |         |                                                                                                                                       |
|                   |          |      | - l5_fb     |         |                                                                                                                                       |
|                   |          |      | - l5_ftb    |         |                                                                                                                                       |
|                   |          |      | - l6        |         |                                                                                                                                       |
|                   |          |      | - l6_ft     |         |                                                                                                                                       |
|                   |          |      | - l6_fb     |         |                                                                                                                                       |
|                   |          |      | - l6_ftb    |         |                                                                                                                                       |
|                   |          |      | - l7_e0     |         |                                                                                                                                       |
|                   |          |      | - l7_e0_ft  |         |                                                                                                                                       |
|                   |          |      | - l7_e0_fb  |         |                                                                                                                                       |
|                   |          |      | - l7_e0_ftb |         |                                                                                                                                       |
|                   |          |      | - l7_e1     |         |                                                                                                                                       |
|                   |          |      | - l7_e1_ft  |         |                                                                                                                                       |
|                   |          |      | - l7_e1_fb  |         |                                                                                                                                       |
|                   |          |      | - l7_e1_ftb |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|             SHARE |      0-9 | Bool |         t/f |       f |                                                                                                  Route the share line to the addition |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          TCLK_SEL |      0-9 |  Mux | - off       |     off |                                                                                             Select the clock input to the two top FFs |
|                   |          |      | - clk0      |         |                                                                                                                                       |
|                   |          |      | - clk1      |         |                                                                                                                                       |
|                   |          |      | - clk2      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          TCLR_SEL |      0-9 |  Num | - 0-1       |       0 |                                                                                              Select the aclr input to the two top FFs |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|             TDFF0 |      0-9 |  Mux | - reg       |     reg |                                                                                             Select between LUT and FF for that output |
|                   |          |      | - nlut      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|             TDFF1 |      0-9 |  Mux | - reg       |     reg |                                                                                             Select between LUT and FF for that output |
|                   |          |      | - nlut      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|            TDFF1L |      0-9 |  Mux | - reg       |     reg |                                                                                             Select between LUT and FF for that output |
|                   |          |      | - nlut      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           TEF_SEL |      0-9 |  Mux | - e         |       e |                                                                         Select which input goes to the sdata input of the two top FFs |
|                   |          |      | - f         |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           TPKREG0 |      0-9 | Bool |         t/f |       f |                                                                        Force the top FF of the top half to get its input from tef_sel |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           TPKREG1 |      0-9 | Bool |         t/f |       f |                                                                     Force the bottom FF of the top half to get its input from tef_sel |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         TSCLR_DIS |      0-9 | Bool |         t/f |       f |                                                                                                   Disable sync clear for the top half |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         TSLOAD_EN |      0-9 | Bool |         t/f |       f |                                                                        Select whether to enable the sync load line of the two top FFs |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|    T_FEEDBACK_SEL |      0-9 |  Num | - 0-1       |       0 |                                                                                 Select which of the FFs goes to the top feedback line |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         ACLR0_INV |          | Bool |         t/f |       f |                                                                                            Optional inverter for asynchronous clear 0 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         ACLR0_SEL |          |  Mux | - gin1      |    gin1 |                                                                                      Selects between clock and data for async clear 0 |
|                   |          |      | - clki2     |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         ACLR1_INV |          | Bool |         t/f |       f |                                                                                            Optional inverter for asynchronous clear 1 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         ACLR1_SEL |          |  Mux | - gin0      |    gin0 |                                                                                      Selects between clock and data for async clear 1 |
|                   |          |      | - clki3     |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           BTO_DIS |          | Bool |         t/f |       f |                                                           When disabled, allows carry in/share in from local cell 4 into local cell 5 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|        BYPASS_DIS |          | Bool |         t/f |       t | Bypass skips the top half (lab) or bottom half (mlab) of the cells for the carry and share chains (needs BTO, resp. TTO disabled too) |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLK0_INV |          | Bool |         t/f |       f |                                                                                                         Optional inverter for clock 0 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLK0_SEL |          |  Mux | - clka      |    clka |                                                                          Selects between the two intermedaite clock lines for clock 0 |
|                   |          |      | - clkb      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLK1_INV |          | Bool |         t/f |       f |                                                                                                         Optional inverter for clock 1 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLK1_SEL |          |  Mux | - clka      |    clka |                                                                          Selects between the two intermedaite clock lines for clock 1 |
|                   |          |      | - clkb      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLK2_INV |          | Bool |         t/f |       f |                                                                                                         Optional inverter for clock 2 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLK2_SEL |          |  Mux | - clka      |    clka |                                                                          Selects between the two intermedaite clock lines for clock 2 |
|                   |          |      | - clkb      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLKA_SEL |          |  Mux | - clki0     |   clki0 |                                                                         Selects between clock and data for the clka intermediate line |
|                   |          |      | - gin2      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          CLKB_SEL |          |  Mux | - clki1     |   clki1 |                                                                         Selects between clock and data for the clkb intermediate line |
|                   |          |      | - gin3      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          DFT_MODE |          |  Mux | - off       |      on |                                                                                                                                  TODO |
|                   |          |      | - on        |         |                                                                                                                                       |
|                   |          |      | - dft_pprog |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|            EN0_EN |          | Bool |         t/f |       t |                                                                                            Enables the enable 0 line (else always on) |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          EN0_NINV |          | Bool |         t/f |       t |                                                                                                        Optional inverter for enable 0 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           EN0_SEL |          |  Mux | - gin1      |    gin1 |                                                                                                         Source selection for enable 0 |
|                   |          |      | - gin3      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|            EN1_EN |          | Bool |         t/f |       t |                                                                                            Enables the enable 1 line (else always on) |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          EN1_NINV |          | Bool |         t/f |       t |                                                                                                        Optional inverter for enable 1 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           EN1_SEL |          |  Mux | - gin0      |    gin3 |                                                                                                         Source selection for enable 1 |
|                   |          |      | - gin3      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|            EN2_EN |          | Bool |         t/f |       t |                                                                                            Enables the enable 2 line (else always on) |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          EN2_NINV |          | Bool |         t/f |       t |                                                                                                        Optional inverter for enable 2 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
| EN_SCLK_LOAD_WHAT |          | Bool |         t/f |       f |                                                                                       Unclear, possibly source selection for enable 2 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|  REGSCAN_LATCH_EN |          | Bool |         t/f |       f |                                                                                                                                  TODO |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          SCLR_INV |          | Bool |         t/f |       f |                                                                                               Optional inverter for synchronous clear |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|          SCLR_MUX |          |  Mux | - gin3      |    gin3 |                                                Source selection for sync clear, possibly more subtle (interaction with en2 and sload) |
|                   |          |      | - gin2      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         SLOAD_INV |          | Bool |         t/f |       t |                                                                                                Optional inverter for synchronous load |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|         SLOAD_SEL |          |  Mux | - gin0      |    gin0 |                                                  Source selection for sync load, possibly more subtle (interaction with en2 and sclr) |
|                   |          |      | - gin3      |         |                                                                                                                                       |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
|           TTO_DIS |          | Bool |         t/f |       f |                                             When disabled, allows carry in/share in from the lab at (x, y+1) cell 9 into local cell 0 |
+-------------------+----------+------+-------------+---------+---------------------------------------------------------------------------------------------------------------------------------------+
