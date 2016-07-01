# SDO-AIA
Uncompressing the Image Data
The SSWIDL routine read_sdo.pro can be used to uncompress and read both the header information and the data
into IDL variables:

>> read_sdo,fnames,index,data,/nodata,/noshell

;  copy and paste these commands into your SSWIDL session:

>> result=vso_search(’2011-01-01 1:00’,’2011-01-01 1:01’,inst=’aia’,wave=171,sample=60)
  log=vso_get(result,out_dir=’data’,filenames=fnames,/rice)

After doing so, one can use read_sdo.pro to uncompress the data:
  ;  copy and paste these commands into your SSWIDL session:

>> read_sdo,fnames,index,data
>> help,index,data
>> aia_lct,wave=index(0).wavelnth,/load
>> window,0,xsiz=512,ysiz=512
>> tvscl,rebin(data(*,*,0),[512,512])

>> read_sdo,fnames,index,data,outsize=[700,700]
>> help,index,data

>> read_sdo,fnames,index,data,1024,2048,1200,600
>> help,index,data

Here, a rectangular 1200×600-pixel cutout starting at pixel location (1024,2048) is returned by read_sdo.pro.
Please note that specifying both the cutout information and the OUTSIZE keyword is likely to give unexpected 
results, and is not recommended. 
