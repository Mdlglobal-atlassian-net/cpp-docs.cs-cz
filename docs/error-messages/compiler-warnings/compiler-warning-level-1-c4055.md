---
---
# <a name="compiler-warning-level-1-c4055"></a>C4055 kompilátoru upozornění (úroveň 1)  
  
'Převod': z dat ukazatel 'type1' na ukazatel na funkci 'type2'.  
  
**Zastaralé:** není toto upozornění vygenerovaných Visual Studio 2017 a novější verze.

 Ukazatel dat (pravděpodobně nesprávně) vložena do ukazatel na funkci. Toto je upozornění úrovně 1 v části /Za a úroveň 4 upozornění v části /Ze.  
  
 Následující ukázka generuje C4055:  
  
```C  
// C4055.c  
// compile with: /Za /W1 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
   return (PFUNC)pi;   // C4055  
}  
```  
  
 V části /Ze Toto je upozornění úroveň 4.  
  
```C  
// C4055b.c  
// compile with: /W4 /c  
typedef int (*PFUNC)();  
int *pi;  
PFUNC f() {  
return (PFUNC)pi;   // C4055  
}  
```