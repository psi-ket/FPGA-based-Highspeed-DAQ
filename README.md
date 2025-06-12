# FPGA-based-Highspeed-DAQ

This project implements a DAQ pipeline on an FPGA using both **VHDL** and **Verilog** modules. It includes an ADC interface (AD9215), UART communication, memory controllers, and Fourier/signal computation logic.

---

## ⚙️ What This Project Does

- **Receives analog signals via ADC (AD9215)**
- **Processes signals in hardware**: FFT, squaring, summing, etc.
- **Uses onboard SRAM for temporary storage**
- **Communicates results over UART to a PC**

---

## 🛠 Requirements

- FPGA Board (e.g., Xilinx Spartan-6, Artix-7)
- AD9215 ADC module
- SRAM chip connected to FPGA
- UART-to-USB cable (for serial output)
- FPGA toolchain:
  - Xilinx Vivado or ISE
  - USB JTAG programmer
- Serial terminal software (e.g., PuTTY, TeraTerm)
- Power supply for the board

---

## 🚀 How to Use

### 1. **Load the Bitstream**

1. Open Xilinx Vivado or ISE.
2. Open or create a project and import:
   - All files in `/VHDL` and `/Verilog`
   - Set `TOP.v` as the top-level module.
3. Run **Synthesis → Implementation → Bitstream Generation**.
4. Program the FPGA with `TOP.bit` using a USB JTAG cable.

---

### 2. **Connect the Hardware**

- Connect the **AD9215** module's digital output to FPGA input pins.
- Ensure **SRAM** chip is properly wired to its respective pins.
- Connect **UART TX** from FPGA to PC via USB-UART converter.
- Power on the FPGA board.

---

### 3. **Run & Observe**

- Open a serial terminal on your PC (e.g., PuTTY).
- Set baud rate: **115200** (8 data bits, no parity, 1 stop bit).
- After FPGA starts, you should see:
  - **Serial output** with processed data (FFT, etc.)
  - Optionally, status/debug info from the serial interface.

---

## 🔍 Customization

You can customize:

- **Signal processing behavior**: e.g., modify `Fourier.v` or `Sum.v`
- **UART packet format**: tweak `Serial_tx.vhd`
- **Clock behavior**: adjust `pll_loop.v` or `ADC_clock_mux.v`

---

## 💡 Tips

- Use a logic analyzer to verify pin-level signals.
- Simulate modules individually before full synthesis.
- Match voltage levels between FPGA and ADC/SRAM.


