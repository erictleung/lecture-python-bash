all : file1_count.txt file2_count.txt file3_count.txt

create :
	echo -e "1\n2\n3\n4\n5\n6" > file1.txt
	echo -e "Hello, world!" > file2.txt
	echo -e "We're learning bash programming!" > file3.txt

%_count.txt : %.txt
	wc $< > $@

clean :
	rm file*
