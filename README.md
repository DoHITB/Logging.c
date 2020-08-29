# Logging.c
Yet another logging module made on C. It supports file output!

## How to use
First, set an information-level for your output. For example:

    int INFORMATIONAL = 0;
    int WARNING = 1;
    int ERROR = 2;
    int SEVERE = 3;
    
Then, you can optionally set an output file:

    setFile("path\\to\\your\\file.log");
    
Finally, start your log session:

    activateLog(WARNING);
    
Now you can start ```_log()```ing things (with ```printf()``` format):

    int i = 10;
    
    _log("This is the value for i: %i", INFORMATIONAL, i);
    
Just put your text, ```printf()``` style, putting **always** level variable on the first position.
The output will contain ```clock()``` value, followed by the passed information:

    220:    This is the value for i: 10
    
Dou you want it more clear? Just use ```inFunction()``` and ```outFunction()``` to increase or decrease tabulation:

    void main() {
        int INFORMATIONAL = 0;
        int WARNING = 1;
        int ERROR = 2;
        int SEVERE = 3;
        int MUST = 999;
    
        int i = 0;
    
        activateLog(INFORMATIONAL);
    
        for (; i < 10; i++) {
            _log("This is the value for i: %i", INFORMATIONAL, i);
            inFunction();
        }
    
        return;
    }
    
Will return something like:

    157:    This is the value for i: 0
            159:    This is the value for i: 1
                    160:    This is the value for i: 2
                            162:    This is the value for i: 3
                                    163:    This is the value for i: 4
                                            165:    This is the value for i: 5
                                                    167:    This is the value for i: 6
                                                            168:    This is the value for i: 7
                                                                    170:    This is the value for i: 8
                                                                            171:    This is the value for i: 9
                                                                            
You can stop logging with ```deactivateLog()``` function, at any time.

So, it's simple and fast. Easy to use and ready to go.

