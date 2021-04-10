# need-ttk-help
too many ttk.button created

from tkinter import *
from tkinter import ttk
class APP:
    def __init__(self, master):
        master.title('APP')
        master.resizable(False, False)

        self.style = ttk.Style()

        self.frame_header = ttk.Frame(master)
        self.frame_header.pack()

        self.frame_stations = ttk.Frame(master)
        self.frame_stations.pack()
        # default style and text of button
        self.style.configure('n1_on.TButton', foreground='#d2d2d2',font=('Arial', 15,'bold'))
        self.style.configure('n1_off.TButton', foreground='#d2d2d2', font=('Arial',15,'bold'))
        self.style.configure('n2_on.TButton',  foreground='#d2d2d2',font=('Arial', 15,'bold'))
        self.style.configure('n2_off.TButton', foreground='#d2d2d2', font=('Arial', 15,'bold'))
        # changes state (disabled) and font color when clocked
        self.style.map('n1_on.TButton', foreground=[('disabled','green')])
        self.style.map('n1_off.TButton', foreground=[('disabled','red')])
        self.style.map('n2_off.TButton', foreground=[('disabled','red')])
        self.style.map('n2_on.TButton', foreground=[('disabled','green')])

        ttk.Label(self.frame_stations, text="BUTTONS").grid(row=0, column=1, columnspan=2, padx=5)
        #buttons created adn location
        self.n1_on = ttk.Button(self.frame_stations, text='ON', style='n1_on.TButton', command=self.n1_on_state,)
        self.n1_on.grid(row=1, column=1)
        self.n2_on = ttk.Button(self.frame_stations, text='ON', style='n2_on.TButton', command=self.n2_on_state)
        self.n2_on.grid(row=2, column=1)

        self.n1_off = ttk.Button(self.frame_stations, text='OFF', style= 'n1_off.TButton', command=self.n1_off_state)
        self.n1_off.grid(row=1, column=2)
        self.n2_off= ttk.Button(self.frame_stations, text='OFF', style='n2_off.TButton', command=self.n2_off_state)
        self.n2_off.grid(row=2, column=2)

    def n1_on_state(self):
        print('n1 turned on')
        self.n1_on.state(['disabled'])
        self.n1_off.state(['!disabled'])

    def n2_on_state(self):
        print('n2 turned on')
        self.n2_on.state(['disabled'])
        self.n2_off.state(['!disabled'])

    def n1_off_state(self):
        print('n1_turned off')
        self.n1_on.state(['!disabled'])
        self.n1_off.state(['disabled'])

    def n2_off_state(self):
        print('n2 turned off')
        self.n2_on.state(['!disabled'])
        self.n2_off.state(['disabled'])
        
        def main():
    root = Tk()
    app = APP(root)
    root.mainloop()


if __name__ == '__main__': main()
