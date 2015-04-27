# Cse460
#ifndef ASSEMBLER_H
#define ASSEMBLER_H

#include <fstream>
#include <sstream>
#include <map>
#include <iostream>
#include <cstring>
#include <cctype>
#include <cstdlib>
#include <stdexcept>

using namespace std;


class NullPointerException: public runtime_error {
public:
	NullPointerException(): runtime_error("Null Pointer!") { }
};

class Assembler {
private:
	typedef void (Assembler::*FP)(string);
	void transcribe(int code); //Writes the binary to the .o file

	//declaring all instructions
	void _load(string s);
	void _loadi(string s);
	void _store(string s);
	void _add(string s);	
	void _addi(string s);
	void _addc(string s);
	void _addci(string s);
	void _sub(string s);
	void _subi(string s);
	void _subc(string s);
	void _subci(string s);
	void _and(string s);
	void _andi(string s);
	void _xor(string s);
	void _xori(string s);
	void _compl(string s);
	void _shl(string s);
	void _shla(string s);
	void _shr(string s);
	void _shra(string s);
	void _compr(string s);
	void _compri(string s);
	void _getstat(string s);
	void _putstat(string s);
	void _jump(string s);
	void _jumpl(string s);
	void _jumpe(string s);
	void _jumpg(string s);
	void _call(string s);
	void _return(string s);
	void _read(string s);
	void _write(string s);
	void _halt(string s);
	void _noop(string s);

	map<string, FP> instr; //map FN 
	string outputFile, inputFile;
public:
	Assembler();
	void assemble(string fileName);
};


#endif
