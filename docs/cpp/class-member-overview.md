---
title: Přehled členů třídy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd280255afe98aa5ca512c63bb00623891eafc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="class-member-overview"></a>Přehled členů třídy
Třídě nebo struktuře se skládá z její členy. Činnost prováděnou třídu provádí jeho členské funkce. Stav, který udržuje je uložen v jeho datové členy. Inicializace členů je potřeba konstruktory a čištění pracovní například uvolnění paměti a uvolnění prostředků se provádí destruktory. C ++ 11 a novější datové členy můžete (a obvykle by měl) inicializovat v místě deklarace.  
  
## <a name="kinds-of-class-members"></a>Typy členů tříd  
 Úplný seznam kategorií člen je následující:  
  
-   [Speciální členské funkce](special-member-functions.md).  
  
-   [Přehled členských funkcí](overview-of-member-functions.md).  
  
-   [Datové členy](static-members-cpp.md) včetně předdefinovaných typů a jiným uživatelem definované typy.  
  
-   Operátory  
  
-   [Vnořené deklarace tříd](nested-class-declarations.md) a.)  
  
-   [Sjednocení](unions.md)  
  
-   [Výčty](../cpp/enumerations-cpp.md).  
  
-   [Bit pole](../cpp/cpp-bit-fields.md).  
  
-   [Přátel](../cpp/friend-cpp.md).  
  
-   [Aliasy a definice TypeDef](../cpp/aliases-and-typedefs-cpp.md).  
  
    > [!NOTE]
    >  Přátelé jsou zahrnuty v předchozím seznamu, protože jsou obsaženy v deklaraci třídy. Nejsou však skutečnými členy třídy, protože nejsou v oboru třídy.  
  
## <a name="example-class-declaration"></a>Příklad deklaraci třídy  
 Následující příklad ukazuje deklaraci jednoduché třídy:  
  
```  
// TestRun.h  
  
class TestRun  
{  
    // Start member list.  
  
    //The class interface accessible to all callers.  
public:  
    // Use compiler-generated default constructor:  
    TestRun() = default;   
    // Don't generate a copy constructor:  
    TestRun(const TestRun&) = delete;    
    TestRun(std::string name);  
    void DoSomething();  
    int Calculate(int a, double d);  
    virtual ~TestRun();  
    enum class State { Active, Suspended };  
  
    // Accessible to this class and derived classes only.  
protected:  
    virtual void Initialize();  
    virtual void Suspend();  
    State GetState();  
  
    // Accessible to this class only.  
private:  
    // Default brace-initialization of instance members:  
    State _state{ State::Suspended };   
    std::string _testName{ "" };   
    int _index{ 0 };  
  
    // Non-const static member:  
    static int _instances;  
    // End member list.  
};  
  
// Define and initialize static member.  
int TestRun::_instances{ 0 };  
```  
  
## <a name="member-accessibility"></a>Člen usnadnění  
 Členy třídy jsou deklarované v seznamu členů. Seznam členů třídy mohou být rozděleny na libovolný počet `private`, `protected` a **veřejné** částech pomocí klíčových slov známé jako specifikátory přístupu.  Dvojtečkou **:** musí následovat specifikátor přístup.  Tyto části nemusejí být souvislé, to znamená, že některé z těchto klíčových slov se mohou v seznamu členů objevit několikrát.  Klíčové slovo určuje přístup všech členů, dokud se neobjeví další specifikátor přístupu nebo uzavírací složená závorka. Další informace najdete v tématu [ovládací prvek přístupu členů (C++)](../cpp/member-access-control-cpp.md).  
  
## <a name="static-members"></a>Statické členy  
 Datový člen může být deklarován jako statický, což znamená, že všechny objekty třídy mají přístup na stejnou kopii. Členské funkce může být deklarován jako statický, v takovém případě je přístup jenom k členy statických dat třídy (a neobsahuje žádné *to* ukazatel). Další informace najdete v tématu [statické členy Data](../cpp/static-members-cpp.md).  
  
## <a name="special-member-functions"></a>Speciální členské funkce  
 Speciální členské funkce jsou funkce, které jsou automaticky poskytované kompilátorem, pokud nezadáte je ve zdrojovém kódu.  
  
1.  Výchozí konstruktor  
  
2.  Kopírovací konstruktor  
  
3.  **(C ++ 11)**  Konstruktor move  
  
4.  Operátor přiřazení kopie  
  
5.  **(C ++ 11)**  Operátor přiřazení přesunutí  
  
6.  Destruktor  
  
Další informace najdete v tématu [speciální členské funkce](../cpp/special-member-functions.md).
  
## <a name="memberwise-initialization"></a>Memberwise inicializace  
 C ++ 11 a novější může obsahovat nestatické členské deklarátory inicializátory.  
  
```  
  
class CanInit  
{  
public:  
    long num {7};       // OK in C++11  
    int k = 9;          // OK in C++11  
    static int i = 9; // Error: must be defined and initialized  
                      // outside of class declaration.  
  
    // initializes num to 7 and k to 9  
    CanInit(){}  
  
    // overwrites original initialized value of num:  
    CanInit(int val) : num(val) {}  
};  
int main()  
{  
}  
```  
  
 Pokud člen je přiřazenou hodnotu do konstruktoru, tato hodnota přepíše hodnotu, která byla člen inicializuje v místě deklarace.  
  
 Existuje pouze jedna kopie sdílených statických datových členů pro všechny objekty typu dané třídy. Statické datové členy musejí být definovány a mohou být inicializovány v rozsahu souboru. (Další informace o členy statických dat najdete v tématu [statické členy Data](../cpp/static-members-cpp.md).) Následující příklad ukazuje, jak provést tyto inicializace:  
  
```  
// class_members2.cpp  
class CanInit2  
{  
public:  
    CanInit2() {} // Initializes num to 7 when new objects of type   
                 //  CanInit are created.  
    long     num {7};  
    static int i;  
    static int j;  
};  
  
// At file scope:  
  
// i is defined at file scope and initialized to 15.  
// The initializer is evaluated in the scope of CanInit.  
int CanInit2::i = 15;  
  
// The right side of the initializer is in the scope   
// of the object being initialized  
int CanInit2::j = i;  
```  
  
> [!NOTE]
>  Název třídy `CanInit2` musí předcházet identifikátor `i`, čímž určíte, že definovaný identifikátor `i` je členem třídy `CanInit2`.  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)
