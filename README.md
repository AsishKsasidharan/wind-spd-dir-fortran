# wind-spd-dir-fortran
This project contains a fortran code for Computing Wind Speed and Direction from u and v wind components.
#This code is for computing wind speed and direction form a file contains U and V components (column-wise)

U=u Component of the wind
v=v Component of the wind
rs= Wind speed
rd= Wind direction	        
		
		
		
		
		
		real u,v,rs,rd
	        open (10,file='	inputfile.txt',status='old') #insert your input file name here
	        open(12,file='outputfile.txt',status='unknown')#insert your output file name here
                pi=atan(1.0e00)*4.0
  	        rad=pi/180.0
  
       c100	read(10,*,end=98)month,date,u,v
       100	read(10,*,end=98)u,v
       c	swh=0
       c	u=-1.140583333
       c	v=-0.1215

	         rs=sqrt((u*u)+(v*v))
	         if (v.eq.0.) then
	         if (u.gt.0)then
		       rd = 90
	         else
	         rd=270
	         endif
		       go to 101
           end if
	       
          rd=(atan(u/v))/rad
	        if((u.ge.0.).and.(v.lt.0.))
          +     rd=rd+180.
	        if((u.lt.0.).and.(v.lt.0.))
          +     rd=rd+180.
	        if((u.lt.0.).and.(v.ge.0.))
          +     rd=rd+360.
	        if((u.eq.0.).and.(v.eq.0.))
          +     rd=0.
          101 	  rd=rd+180.0
	        if(rd.ge.360.0) rd=rd-360.0

          c	write(12,*)rs,rd
	      	write(12,*)u,v,rs,rd



         goto 100
     98   close(10) 
     99   close(11)
	        stop
	        end
