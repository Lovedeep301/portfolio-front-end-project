# portfolio-Hospital management system

import tkinter as tk
from tkinter import ttk
from tkinter import messagebox
from tkinter import StringVar
import random
import time
import datetime
import mysql.connector

class Hospital:
    def __init__(self, root):
        self.root = root
        self.root.title("Hospital Management System")
        self.root.geometry("1350x700+0+0")
        
        # Variables
        self.Nameoftablets = StringVar()
        self.ref = StringVar()
        self.Dose = StringVar()
        self.NumberofTablets = StringVar()
        self.Lot = StringVar()
        self.Issuedate = StringVar()
        self.ExpDate = StringVar()
        self.DailyDose = StringVar()
        self.sideEfect = StringVar()
        self.FurtherInformation = StringVar()
        self.StorageAdvice = StringVar()
        self.DrivingUsingMachine = StringVar()
        self.HowToUseMedication = StringVar()
        self.PatientId = StringVar()
        self.nhsNumber = StringVar()
        self.PatientName = StringVar()
        self.DateOfBirth = StringVar()
        self.PatientAddress = StringVar()
        self.BloodPressure = StringVar()
        self.Medicine = StringVar()

        lbltitle = tk.Label(self.root, bd=20, relief=tk.RIDGE, text="HOSPITAL MANAGEMENT SYSTEM", fg="red", bg="white", font=("times new roman", 50, "bold"))
        lbltitle.pack(side=tk.TOP, fill=tk.X)

        # Data frame
        Dataframe = tk.Frame(self.root, bd=20, relief=tk.RIDGE)
        Dataframe.place(x=0, y=130, width=1350, height=400)

        DataframeLeft = tk.LabelFrame(Dataframe, bd=10, relief=tk.RIDGE, padx=10, font=("times new roman", 12, "bold"), text="Patient Information")
        DataframeLeft.place(x=0, y=5, width=670, height=350)

        DataframeRight = tk.LabelFrame(Dataframe, bd=10, relief=tk.RIDGE, padx=10, font=("times new roman", 12, "bold"), text="Prescription")
        DataframeRight.place(x=680, y=5, width=650, height=350)

        # Buttons frame
        Buttonframe = tk.Frame(self.root, bd=20, relief=tk.RIDGE)
        Buttonframe.place(x=0, y=530, width=1350, height=70)

        # Details frame
        Detailsframe = tk.Frame(self.root, bd=20, relief=tk.RIDGE)
        Detailsframe.place(x=0, y=600, width=1350, height=190)

        # DataframeLeft
        lblNameTablet = tk.Label(DataframeLeft, text="Name of Tablet:", font=("arial", 12, "bold"), padx=2, pady=6)
        lblNameTablet.grid(row=0, column=0, sticky=tk.W)

        comNametablet = ttk.Combobox(DataframeLeft, textvariable=self.Nameoftablets, font=("arial", 12, "bold"), width=33)
        comNametablet['values'] = ("Nice", "Corona Vaccine", "Acetaminophen", "Adderall", "Amlodipine", "Ativan")
        comNametablet.grid(row=0, column=1)

        lblref = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Reference No:", padx=2, pady=6)
        lblref.grid(row=1, column=0, sticky=tk.W)
        txtref = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.ref, width=35)
        txtref.grid(row=1, column=1)

        lblDose = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Dose:", padx=2, pady=6)
        lblDose.grid(row=2, column=0, sticky=tk.W)
        txtDose = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.Dose, width=35)
        txtDose.grid(row=2, column=1)

        lblNoOftablets = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="No Of Tablets:", padx=2, pady=6)
        lblNoOftablets.grid(row=3, column=0, sticky=tk.W)
        txtNoOftablets = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.NumberofTablets, width=35)
        txtNoOftablets.grid(row=3, column=1)

        lblLot = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Lot:", padx=2, pady=6)
        lblLot.grid(row=4, column=0, sticky=tk.W)
        txtLot = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.Lot, width=35)
        txtLot.grid(row=4, column=1)

        lblissueDate = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Issue Date:", padx=2, pady=6)
        lblissueDate.grid(row=5, column=0, sticky=tk.W)
        txtissueDate = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.Issuedate, width=35)
        txtissueDate.grid(row=5, column=1)

        lblExpDate = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Exp Date:", padx=2, pady=6)
        lblExpDate.grid(row=6, column=0, sticky=tk.W)
        txtExpDate = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.ExpDate, width=35)
        txtExpDate.grid(row=6, column=1)

        lblDailyDose = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Daily Dose:", padx=2, pady=6)
        lblDailyDose.grid(row=7, column=0, sticky=tk.W)
        txtDailyDose = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.DailyDose, width=35)
        txtDailyDose.grid(row=7, column=1)

        lblSideEffect = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Side Effect:", padx=2, pady=6)
        lblSideEffect.grid(row=8, column=0, sticky=tk.W)
        txtSideEffect = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.sideEfect, width=35)
        txtSideEffect.grid(row=8, column=1)

        lblFurtherinfo = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Further Information", padx=2, pady=6)
        lblFurtherinfo.grid(row=0, column=2, sticky=tk.W)
        txtFurtherinfo = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.FurtherInformation, width=35)
        txtFurtherinfo.grid(row=0, column=3)

        lblBloodPressure = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Blood Pressure", padx=2, pady=6)
        lblBloodPressure.grid(row=1, column=2, sticky=tk.W)
        txtBloodPressure = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.BloodPressure, width=35)
        txtBloodPressure.grid(row=1, column=3)

        lblStorage = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Storage Advice:", padx=2, pady=6)
        lblStorage.grid(row=2, column=2, sticky=tk.W)
        txtStorage = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.StorageAdvice, width=35)
        txtStorage.grid(row=2, column=3)

        lblMedicine = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Medication", padx=2, pady=6)
        lblMedicine.grid(row=3, column=2, sticky=tk.W)
        txtMedicine = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.Medicine, width=35)
        txtMedicine.grid(row=3, column=3)

        lblPatientId = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Patient Id", padx=2, pady=6)
        lblPatientId.grid(row=4, column=2, sticky=tk.W)
        txtPatientId = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.PatientId, width=35)
        txtPatientId.grid(row=4, column=3)

        lblNhsNumber = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="NHS Number", padx=2, pady=6)
        lblNhsNumber.grid(row=5, column=2, sticky=tk.W)
        txtNhsNumber = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.nhsNumber, width=35)
        txtNhsNumber.grid(row=5, column=3)

        lblPatientname = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Patient Name", padx=2, pady=6)
        lblPatientname.grid(row=6, column=2, sticky=tk.W)
        txtPatientname = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.PatientName, width=35)
        txtPatientname.grid(row=6, column=3)

        lblDateOfBirth = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Date Of Birth", padx=2, pady=6)
        lblDateOfBirth.grid(row=7, column=2, sticky=tk.W)
        txtDateOfBirth = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.DateOfBirth, width=35)
        txtDateOfBirth.grid(row=7, column=3)

        lblPatientAddress = tk.Label(DataframeLeft, font=("arial", 12, "bold"), text="Patient Address", padx=2, pady=6)
        lblPatientAddress.grid(row=8, column=2, sticky=tk.W)
        txtPatientAddress = tk.Entry(DataframeLeft, font=("arial", 13, "bold"), textvariable=self.PatientAddress, width=35)
        txtPatientAddress.grid(row=8, column=3)

        # DataframeRight
        self.txtPrescription = tk.Text(DataframeRight, font=("arial", 12, "bold"), width=45, height=16, padx=2, pady=6)
        self.txtPrescription.grid(row=0, column=0)

        # Buttons
        btnPrescription = tk.Button(Buttonframe, text="Prescription", bg="green", fg="red", font=("arial", 12, "bold"), width=23, height=1, pady=6)
        btnPrescription.grid(row=0, column=0)

        btnPrescriptiondata = tk.Button(Buttonframe, text="Prescription Data", bg="green", fg="red", font=("arial", 12, "bold"), width=23, height=1, pady=6)
        btnPrescriptiondata.grid(row=0, column=1)

        btnupdate = tk.Button(Buttonframe, text="Update", bg="green", fg="red", font=("arial", 12, "bold"), width=23, height=1, pady=6)
        btnupdate.grid(row=0, column=2)

        btndelete = tk.Button(Buttonframe, text="Delete", bg="green", fg="red", font=("arial", 12, "bold"), width=23, height=1, pady=6)
        btndelete.grid(row=0, column=3)

        btnclear = tk.Button(Buttonframe, text="Clear", bg="green", fg="red", font=("arial", 12, "bold"), width=23, height=1, pady=6)
        btnclear.grid(row=0, column=4)

        btnexit = tk.Button(Buttonframe, text="Exit", bg="green", fg="red", font=("arial", 12, "bold"), width=23, height=1, pady=6)
        btnexit.grid(row=0, column=5)

        # Table
        scroll_x = ttk.Scrollbar(Detailsframe, orient="horizontal")
        scroll_y = ttk.Scrollbar(Detailsframe, orient="vertical")
        self.hospital_table = ttk.Treeview(Detailsframe, columns=("nameoftable", "ref", "dose", "nooftablets", "lot", "issuedate", "expdate", "dailydose", "storage", "nhsnumber", "pname", "dob", "address"), xscrollcommand=scroll_x.set, yscrollcommand=scroll_y.set)
        scroll_x.pack(side="bottom", fill="x")
        scroll_y.pack(side="right", fill="y")

        scroll_x.config(command=self.hospital_table.xview)
        scroll_y.config(command=self.hospital_table.yview)

        self.hospital_table.heading("nameoftable", text="Name Of Tablet")
        self.hospital_table.heading("ref", text="Reference No.")
        self.hospital_table.heading("dose", text="Dose")
        self.hospital_table.heading("nooftablets", text="No Of Tablets")
        self.hospital_table.heading("lot", text="Lot")
        self.hospital_table.heading("issuedate", text="Issue Date")
        self.hospital_table.heading("expdate", text="Exp Date")
        self.hospital_table.heading("dailydose", text="Daily Dose")
        self.hospital_table.heading("storage", text="Storage")
        self.hospital_table.heading("nhsnumber", text="NHS Number")
        self.hospital_table.heading("pname", text="Patient Name")
        self.hospital_table.heading("dob", text="DOB")
        self.hospital_table.heading("address", text="Address")

        self.hospital_table["show"] = "headings"

        self.hospital_table.column("ref", width=100)
        self.hospital_table.column("dose", width=100)
        self.hospital_table.column("nooftablets", width=100)
        self.hospital_table.column("lot", width=100)
        self.hospital_table.column("issuedate", width=100)
        self.hospital_table.column("expdate", width=100)
        self.hospital_table.column("dailydose", width=100)
        self.hospital_table.column("storage", width=100)
        self.hospital_table.column("nhsnumber", width=100)
        self.hospital_table.column("pname", width=100)
        self.hospital_table.column("dob", width=100)
        self.hospital_table.column("address", width=100)

        self.hospital_table.pack(fill="both", expand=1)

    # Functionality Declaration
    def iPrescriptionData(self):
        if self.Nameoftablets.get() == "" or self.ref.get() == "":
            messagebox.showerror("Error", "All Fields Are Required")
        else:
            conn = mysql.connector.connect(host="localhost", username="root", password="root", database="mydata")
            my_cursor = conn.cursor()
            # Add the SQL query and cursor execution here
            conn.close()
root = tk.Tk()
ob = Hospital(root)
root.mainloop()

