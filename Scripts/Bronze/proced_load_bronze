/*
===============================================================================
Stored Procedure: Load Bronze Layer (Source -> Bronze)
===============================================================================
Script Purpose:
    This stored procedure loads data into the 'bronze' schema from external CSV files. 
    It performs the following actions:
    - Truncates the bronze tables before loading data.
    - Uses the `BULK INSERT` command to load data from csv Files to bronze tables.

Usage Example:
    EXEC bronze.load_bronze;
===============================================================================
*/

Create or ALTER   Procedure [bronze].[load_bronze] AS
Begin
	DECLARE @start_time DATETIME, @end_time DATETIME, @batch_start_time DATETIME, @batch_end_time DATETIME;
	Begin Try
		SET @batch_start_time = GETDATE();
		Print '************************************************************'
		print 'Loading Bronze Layer'
		Print '************************************************************'

		Print '++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++'
		print 'Loading CRM Tables'
		Print '++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++'

		SET @start_time = GETDATE();
		Print '>> Truncating Table:crm_cust_info'
		Truncate table [bronze].[crm_cust_info];
		Print '>> Inserting Data Into Table:crm_cust_info'
		Bulk Insert [bronze].[crm_cust_info]
		from "C:\Users\maham\Downloads\SQL-Data-Warehouse-Project\Datasets\source_crm\cust_info.csv"
		with(
		Firstrow=2,
		fieldterminator=',',
		Tablock
		);
		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
		PRINT '>> -------------';

		SET @start_time = GETDATE();
		Print '>> Truncating Table:crm_prd_info'
		Truncate table [bronze].[crm_prd_info];
		Print '>> Inserting Data Into Table:crm_prd_info'
		Bulk Insert [bronze].[crm_prd_info]
		from "C:\Users\maham\Downloads\SQL-Data-Warehouse-Project\Datasets\source_crm\prd_info.csv"
		with(
		Firstrow=2,
		fieldterminator=',',
		Tablock
		);
		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
		PRINT '>> -------------';

    SET @start_time = GETDATE();
		Print '>> Truncating Table:crm_sales_details'
		Truncate table [bronze].[crm_sales_details];
		Print '>> Inserting Data Into Table:crm_sales_details'
		Bulk Insert [bronze].[crm_sales_details]
		from "C:\Users\maham\Downloads\SQL-Data-Warehouse-Project\Datasets\source_crm\sales_details.csv"
		with(
		Firstrow=2,
		fieldterminator=',',
		Tablock
		);
		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
		PRINT '>> -------------';

		Print '++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++'
		print 'Loading ERP Tables'
		Print '++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++'

		SET @start_time = GETDATE();
		Print '>> Truncating Table:erp_cust_az12'
		Truncate table [bronze].[erp_cust_az12];
		Print '>> Inserting Data Into Table:erp_cust_az12'
		Bulk Insert [bronze].[erp_cust_az12]
		from "C:\Users\maham\Downloads\SQL-Data-Warehouse-Project\Datasets\source_erp\CUST_AZ12.csv"
		with(
		Firstrow=2,
		fieldterminator=',',
		Tablock
		);
		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
		PRINT '>> -------------';

		SET @start_time = GETDATE();
		Print '>> Truncating Table:erp_loc_a101'
		Truncate table [bronze].[erp_loc_a101];
		Print '>> Inserting Data Into Table:erp_loc_a101'
		Bulk Insert [bronze].[erp_loc_a101]
		from "C:\Users\maham\Downloads\SQL-Data-Warehouse-Project\Datasets\source_erp\LOC_A101.csv"
		with(
		Firstrow=2,
		fieldterminator=',',
		Tablock
		);
		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
		PRINT '>> -------------';

		SET @start_time = GETDATE();
		Print '>> Truncating Table:erp_px_cat_g1v2'
		Truncate table [bronze].[erp_px_cat_g1v2];
		Print '>> Inserting Data Into Table:erp_px_cat_g1v2'
		Bulk Insert [bronze].[erp_px_cat_g1v2]
		from "C:\Users\maham\Downloads\SQL-Data-Warehouse-Project\Datasets\source_erp\PX_CAT_G1V2.csv"
		with(
		Firstrow=2,
		fieldterminator=',',
		Tablock
		);
		SET @end_time = GETDATE();
		PRINT '>> Load Duration: ' + CAST(DATEDIFF(second, @start_time, @end_time) AS NVARCHAR) + ' seconds';
		PRINT '>> -------------';

		SET @batch_end_time = GETDATE();
		PRINT '=========================================='
		PRINT 'Loading Bronze Layer is Completed';
        PRINT '   - Total Load Duration: ' + CAST(DATEDIFF(SECOND, @batch_start_time, @batch_end_time) AS NVARCHAR) + ' seconds';
		PRINT '=========================================='
	End Try
	Begin Catch
		Print 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
		Print 'Error During Loading Bronze Layer'
		Print 'Error Message'+ ERROR_MESSAGE();
		Print 'Error Message'+ CAST (ERROR_NUMBER() AS Nvarchar);
		Print 'Error Message'+ERROR_STATE();
		Print 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
	End Catch
End

