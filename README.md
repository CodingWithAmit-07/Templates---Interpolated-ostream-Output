# Templates---Interpolated-ostream-Output
 The C++ &lt;iostream> is arguably more idiomatic for C++, but is harder to read and type (at least for me) than C's printf(). C's printf() is not extensible and not type-safe, however. This is an attempt to get the best of both worlds.  Write a function template named Interpolate that will make the below work. Each argument will be output when its corresponding % is encountered in the format string. All output should be ultimately done with the appropriate overloaded &lt;&lt; operator directly to the actual std::ostream object. In other words, you should not build a string, then output that.  A \% sequence should output a percent sign.      SomeArbitraryClass obj;     int i = 1234;     double x = 3.14;     std::string str("foo");     std::cout &lt;&lt; Interpolate(R"(i=%, x1=%, x2=%\%, str1=%, str2=%, obj=%)", i, x, 1.001, str, "hello", obj) &lt;&lt; std::endl;  If there is a mismatch between the number of percent signs and the number of arguments to output, throw an exception of type cs540::WrongNumberOfArgs.  Support the I/O manipulators listed here. An I/O manipulator should not “consume” a percent sign, unless it actually adds something to the output stream (std::ends, std::endl, std::put_money, etc.). You should be able to support these without creating a partial specialization or overloaded function template for every single manipulator. The ffr() function is a helper function to force the instantiation of manipulators that are actually function templates. If you don't need it, that is fine, and in fact even better. Otherwise, you'll need to implement it. .  You might find std::integer_sequence and std::tuple to be of help. Also, std::enable_if (SFINAE). 