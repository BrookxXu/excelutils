# excelutils
This is an java excelutil cope with Spire.xls,make sure u have this jar in ur project.

# Use the annotation @ExcelProp to mark a class as a 'excel class' which defines the properties below:
String templateName();

int sheetIndex() default 0;

int startRow() default 0;

int colSize();
 
 templateName means your excel template name,it can include absolude path and if it does,then u don't need to use methods with argument 'path' in the main util class.
 
 sheetIndex means the index of the sheet u want to map to this class.
 
 startRow defines the start row index in your sheet in case u might have some rows taken by titles etc.
 
 colSize means the max column length of the excel data could cover.
 
# Use @ColNum to determine the column index a field mapped to:
 int value();
 
# Use @Rownum to mark a field as row number :
 it works when u use the reading method in the main util class, and the field will be assigned of the row number.
 
 it's optional.
 
# Use interface ExcelModify to add your own operations before gererate an excel.
 
# Use class ExcelValue to assign some values of the cells of an excel file(the template).
 private int sheetIndex;
 
 private int rownum;
 
 private int colnum;
 
 private String value;
 
 Well the field name is clear enough i think.
 
# Use ExcelTool (mentioned above 'main util class') to generate or read an excel:
 public static <T> Workbook generateWorkbook(List<T> data,Class<T> clazz,String path,ExcelModify doBefore)
 
 This is the mother method to write things into an excel file, it can do most things within the class.So mostly u may just need to use some rewrited method, find it by urself.
 
 public static <T> List<T> readWorkbook(Workbook wb,Class<T> clazz)
 
 This is the reading method, once u defined ur 'excel class', it's easy to use right?
  
