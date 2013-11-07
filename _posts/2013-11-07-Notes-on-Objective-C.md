---
layout: post
title: Notes on Objective-C
---
Notes on Objective-C, from Programming in Objective-C, Fifth Edition



Hello World Program

#import <Foundation/Foundation.h>
int main(int argc, const char * argv[])
{
    @autoreleasepool {
        NSLog(@"Programming is fun");
	NSLog(@"Fun Fun");
    }
    return 0;
}



Basic Data Types(4.1)
Type                      Constant Examples                    NSLog chars
char                      'a','\n'                             %c
short int                 -                                    %hi, %hx, %ho
unsigned short int        -                                    %hu, %hx, %ho
int                       12, -97, oxFFE0, 0177                %i, %x, %o
unsigned int              12u, 100u, 0Xffu                     %u, %x, %o
unsigned long int         12UL, 100ul, 0xffeeUL                %li, %lx, %lo
long long int             0xe5e5e5e5LL, 500ll                  %lli, %llx, %llo
unsigned long long int    12ull, oxffeeull                     %llu, %llx, %llo
float                     12.34f, 3.1e-5f, 0x1.5p10, 0x1p-1    %f, %e, %g, %a
double                    12.34, 3.1e-5, 0x.1p3                %f, %e, %g, %a
long double               12.34L, 3.1e-5l                      %Lf, %Le, %Lg
id                        nil                                  %p



Methods for Working with Dynameic Types(9.1)
Method                                                                     Quesstion or Action
-(BOOL) isKindofClass: class-object                                        Is the object a member of class-object or a descendant?
-(BOOL) isMemberofClass: class-object                                      Is the object a member of class-object?
-(BOOL) respondsToSelector: selector                                       Can the object respond to the method specified by selector?
+(BOOL) instancesRespondToSelector: selector                               Can instances of the specified class respon to selector?
+(BOOL) isSubclassofClass: class-object                                    Is the object of a subclass of the specified class?
-(id) performSelector: selector                                            Apply the method specified by selector
-(id) performSlector: selector withObject: object                          Apply the method specified by selector passing the argument object
-(id) performSelector: selector withObject: object1 withObject: object2    Apply the method specified by selector with the arguments object1 and object2



Exception Handling(P412)
@try{
	//some codes
}
@catch (NSException *exception){
        NSLog(@"Caught %@%@", exception.name, exception.reason);
}



NSArray class's six initialization methods
initWithArray"
initWithArray:copyItems:
initWithContentsofFile:
initWithContentsofURL:
initWithObjects:
initWithObjects:count:



# enum type
enum month { january = 1, february, march, april, may, june, july, august, september, october, november, december };
enum month thisMonth;
thisMonth = february;



Conditional Compliation
#ifdef conditon
    #define A  B
#else
    #define C  D
#endif

#undef E



compoud literal
(struct date){ .month=7, .day=2, year=2011}



NSNumber Creation and Retrieval Methods

