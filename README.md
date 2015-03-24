# Gainful Employment Disclosure Generator
Generate Gainful Employment Disclosure templates from a CSV file.

The supplied `target.csv` file should be generated by your institutional effectiveness people. You can create this with a pull from whichever MSI you are currently using.

# Usage

1. Take a look at the CSV file and ensure that your information matches it. You can change the order of the headers but do not change their names.
2. Run the powershell script: `./ge-template-builder.ps1`

3. Copy the `gainful-employment` folder to our web server.

4. Enjoy.

# Customization

Take a look in `ge-template-builder.ps1` for the following variable block:


    $customProgramName=$item.customProgramName
    $awardLevel=$item.awardLevel
    $tutionAndFees=$item.tutionAndFees
    $booksAndSupplies=$item.booksAndSupplies
    $roomAndBoard="0"
    $roomAndBoardNotOffered="true";
    $numberOfStudentsCompletedProgram=$item.numberOfStudentsCompletedProgram
    $numberOfStudentsCompletedProgramWithDebt=$item.numberOfStudentsCompletedProgramWithDebt
    $isLessThanTenGraduatesReceivedLoan='no'
    if($numberOfStudentsCompletedProgramWithDebt > 9){
        $isLessThanTenGraduatesReceivedLoan='yes'
    }
    $title4MedianDebt=$item.title4MedianDebt
    $privateMedianDebt=$item.privateMedianDebt
    $financingPlanDebt=$item.financingPlanDebt
    $normalTimeToCompleteProgram=$item.normalTimeToCompleteProgram
    $durationTypeInWeeksMonthsYears=$item.durationTypeInWeeksMonthsYears
    $numberOfStudentsCompletedProgramInNormalTime=$item.numberOfStudentsCompletedProgramInNormalTime
    $dateCreated="1/26/2015" #Get-Date -format M/d/yyyy

You can see a few assumptions here. First, we are assuming that we do not offer Room and Board. Second, the date is hardcoded but can be
easily dynamically generated if you want (using the Get-Date feature that's commented out).
