What is this				
How to use				
Processing logic				
What is this				
	This is a handy tool that can help to process the tax report is monthly job.			
		Automatically Processes the tax report generated from SAP		
			- Delete useless information	
				* For tax from salary, delete records that not appears in register (need to provide register)
				* For tax from bonus and stock options, delete records with zero amount
				* For tax from severance payment, delete records with zero tax base
			- Count and output	
				* Records the total tax amount of each tax report
				* Counts the total effective headcount of each tax report
			- Tax location check	
				* Check each employee for the taxlocation
				* Possible to maintain mapping of tax location with company code
			- 1M tax report generation	
				* Fill 1M tax report with given tax reports
				* Auto devide records by company code and tax location
				* Fill in 1M tax distribution
				
How to use				
	Make sure the following documents in the same folder:			
		- This tool		
		- 1M Tax Report template ( If needed )		
		- Tax Reports folder		
		- PayReg folder ( Optional )		
	Put Tax Reports into Tax Reports folder			
		- File name should contain tax type, company code and tax period		
			* Tax type: Salary, Bonus, SO, SP	
			* Company code example: CNX0, CNY1	
			* Tax period example: 201604, 201605	
	Put Register into PayReg folder ( Optional )			
		- File name resembles to tax reports		
			* Company code example: CNX0, CNY1	
			* Pay period example: 201604, 201605	
	Open this tool			
		- Enable content		
		- Press "Start the Tool"		
		- Select period and check the item		
		- Click "Go" to start running		
			* Running speed varies upon CPU and disk	
			* The program might not be responding, but it's working, please be patient	
	Find the output			
		- A new folder will be created in the same directory		
			* The folder is named after running time, format: yyyy.mm.dd_hh.mm.ss	
			* All results are put in this folder	
			* This method ensures no accident if you run the tool several times	
		- "Output Log"		
			* The company code/period/type is based on filename	
			* Excel only supports one format each time, it's .xlsx in this case	
		- "Tax Reports Processed"		
			* For tax location error, tax location in "Output Log" will be Error, the processed cell will be in  yellow	
		- "1M Tax Report"		
			* Termination information need manually added	
			* Special case for tax off need manually added	
Processing logic				
	Start the tool			
		- A little cleaning of the tool self		
		- Record running time		
		- Create output folder		
		- List all tax reports		
		- Find tax reports information in file name		
		- Process RAW tax if selected		
			* The tool only works on which period is "Yes"	
			* Open tax reports one by one	
			* Delete subtotal rows	
			* Delete zero amount rows in bonus/SO	
			* Delete zero tax base rows in SP	
			* Calculate the total headcount and amount	
			* Check if tax location is in scope	
			* Save the new report and record the result	
		- Process Headcount check if selected		
			* If there's no payreg in folder, nothing will happen even if you selected	
			* Open tax from salary reprots only	
			* Check if every employee number exists in payreg	
			* Save the new report and re-calculate headcount	
		- Process 1M tax report if selected		
			* Open the 1M tax report template	
			* Copy data from processed tax reports by PCI/CN12/CN0M by type	
			* Divide PCI data by tax location	
			* Fill in the summary sheet	
			* Delete sheets that no tax occurred	
			* Save the new report	
		- Output Result		
			* Copy process result to a new workbook	
			* Save the result	
