# SortAddAssembler
Assembly project that sorts and adds two integer values.

Additional changes made to fix the top.
#Something going on here.

.data
	message1: .asciiz "Please enter your first number.\n"
	message2: .asciiz "Please enter your second number.\n"
	plus: .asciiz " + "
	equals: .asciiz " = "
	newLine: .asciiz "\n"
	
.text

	#Print the first message to the screen
	
	#Request user input
	li $v0, 4
	la $a0, message1
	syscall
	
	#GETS AN INTEGER FROM THE USER
	li $v0, 5 
	syscall
	
	#store the input
	move $t0, $v0
	
	#Print the second message to the screen
	li $v0, 4
	la $a0, message2
	syscall
	
	#request user input
	li $v0, 5
	syscall
	
	move $t1, $v0
	
	li $v0, 4
	la $a0, newLine
	syscall
	
	#Compare the values
	bgt $t0, $t1, SORT
	
	add $t2, $t1, $t0
	
		li $v0, 1
		move $a0, $t1
		syscall
	
		li $v0, 4
		la $a0, plus
		syscall
	
		li $v0, 1
		move $a0, $t0
		syscall
	
		li $v0, 4
		la $a0, equals
		syscall
	
		li $v0, 1
		move $a0, $t2
		syscall
		
		j EXIT
		
	#FUNCTION FOR SORTING THE INTEGERS
	SORT:
	
		add $t2, $t0, $t1
		
		li $v0, 1
		move $a0, $t0
		syscall
	
		li $v0, 4
		la $a0, plus
		syscall
	
		li $v0, 1
		move $a0, $t1
		syscall
	
		li $v0, 4
		la $a0, equals
		syscall
	
		li $v0, 1
		move $a0, $t2
		syscall
	
	#jump instruction comes here to exit
	EXIT:
		li $v0, 4
		la $a0, newLine
		syscall
	
