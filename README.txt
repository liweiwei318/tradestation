Folder Structure

¢u¢w3rd-party
¢x 
¢u¢wdoc
¢x  ¢|¢webooks
¢u¢wsrc
¢x  ¢u¢wActivityBar
¢x  ¢u¢wFunction
¢x  ¢u¢wIndicator
¢x  ¢u¢wPaintBar
¢x  ¢u¢wProbabilityMap
¢x  ¢u¢wShowMe
¢x  ¢u¢wStrategy
¢x  ¢x  ¢u¢wDayTrading
¢x  ¢x  ¢|¢wSwingTrading
¢x  ¢|¢wTradingApp
¢|¢wTDEProjects


Development Guide

1. Source Code

   The file with extension *.eld is a binary format of TradeStation for EasyLanguage 
   However, the *.eld is a binary format for EasyLanguage.
   In order to avoid the ELD file format or version issue which may cause the import to TDE fail.
   Therefore, we have to provide a pure plain-text source code for each function,indicator...etc

   For example:
      TTM_SEQUEEZE.ELD
      TTM_SEQUEEZE.txt
      
2. Basic Information Document
   Each file should contains the following basic information of each file.
   For example of Function

	#region - Documentation
	{ 
	--------------------------------------------------------------------------------------------------- 
	IDENTIFICATION 
	============== 
	Name:			OpenRangeBreakout 
	Type:			Function
	Version:		01.00.00
	TS Version:		10.0 (Update 46)
	Timeframe:      1~15 min
	Author:         Miller Lai
	Notes:          Caculate Open Range Breakout High/Low
	Description:    This function will caculate the Higheset High and Loweset Low from AM 9:30~10:00
	Input:          Value_H (numericseries) - The High data
	                Value_L (numericseries) - The Low data
	
	Output:         ORB_H (NUMERICREF) - Open Range Breakout High
	                ORB_L (NUMERICREF) - Open Range Breakout Low
	                ORB_M (NUMERICREF) - Open Range Breakout Middle
	Return:         0 is Success.
	} 
	#endregion 


   For example of Indicator

	#region - Documentation
	{ 
	--------------------------------------------------------------------------------------------------- 
	IDENTIFICATION 
	============== 
	Name:			OpenRangeBreakout 
	Type:			Indicator 
	Scaling:        Scalling on same the data
	Version:		01.00.00
	TS Version:		10.0 (Update 46)
	Timeframe:      1~15 min
	Author:         Miller Lai
	Notes:          The open range breakout indicator
	Description:    This indicator draw ORB_H, ORB_L and ORB_M line from AM 10:00~ PM 4:00
	} 
	#endregion 


3. Debug Flag
   usually, the indicator or strategy may be composite by multiple signal other indicators or signal...etc. 
   Therefore, you should provide the debug flag of 'inputs' to show the each signal. 
   
   For example:
		inputs:
			bool debug(false),
			bool show_market_internal_signal(false),
			bool show_spy_signal(false),
			bool show_qqq_signal(false),
			bool show_etf_signal(false);

4. Naming convention
   Function
       If the return value of function is 'bool', the function name should have the prefix "Is"
       
   Indicator
       It should have the debug flag for control the signal.

   Strategy
       DayTrading with prefix "DT_"
           For example:
               DT_SPY_By_MarketInternal.eld
               DT_ES_By_RSI_MACD.eld
           
       SwingTrading with prefix "ST_"
           For example: ST_ETF_By_OptionAnalysis.eld
           
   Variable:
       Boolean Type with prefix "IS_"
       
5. The Function should have the following items:
   * Note - When you create a new Function, you should write the 'Notes' for this function. 
     Otherwise, you can not easily to view the 'Summary' of Dictionary View.
   * ScreenShot - If the function is for drawing something, please help on provide a screenshot (*.png)

6. The Indicator should have the following items:
   * Note - When you create a new Function, you should write the 'Notes' for this function. 
   * ScreenShot - If the indicator is for drawing something, please help on provide a screenshot (*.png)

7. The Strategy should have the following itmes:
   * Note - When you create a new Function, you should write the 'Notes' for this function. 
   * Source Code -
     (*) Description of the strategy logic in the source code
     (*) Supported Timeframe. Example: 1Min, 2Min, 1D, 3D, 1Week, 1Month
     (*) For DayTrading should specify the PreSession or PostSession Time or not.
     (*) Strategy BackTesting Report with Text or ScreenShot which should have the time range for example: 2020-01 to 2020-05

     