---
title: Vnořené deklarace tříd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 247be4e212efbe2b8061deed200a8350b87fc7a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="nested-class-declarations"></a>Vnořené deklarace tříd
Třída může být deklarována v rámci jiné třídy. Tato třída se nazývá „vnořená třída“. Vnořené třídy jsou považovány za součást oboru ohraničující třídy a jsou k dispozici pro použití v daném oboru. Pro odkazování na vnořenou třídu z jiného oboru než jejího bezprostředně ohraničujícího oboru je třeba použít plně kvalifikovaný název.  
  
 Následující příklad ukazuje, jak deklarovat vnořené třídy:  
  
```  
// nested_class_declarations.cpp  
class BufferedIO  
{  
public:  
   enum IOError { None, Access, General };  
  
   // Declare nested class BufferedInput.  
   class BufferedInput  
   {  
   public:  
      int read();  
      int good()  
      {  
         return _inputerror == None;  
      }  
   private:  
       IOError _inputerror;  
   };  
  
   // Declare nested class BufferedOutput.  
   class BufferedOutput  
   {  
      // Member list  
   };  
};  
  
int main()  
{  
}  
```  
  
 `BufferedIO::BufferedInput` a `BufferedIO::BufferedOutput` jsou deklarovány v `BufferedIO`. Tyto názvy tříd nejsou viditelné mimo obor třídy `BufferedIO`. Objekt typu `BufferedIO` však neobsahuje žádné objekty typu `BufferedInput` ani `BufferedOutput`.  
  
 Vnořené třídy mohou přímo použít názvy, názvy typů, názvy statických členů a enumerátory pouze z nadřazené třídy. Pro použití názvů ostatních členů třídy je nutné použít ukazatele, odkazy nebo názvy objektů.  
  
 V předchozím příkladu `BufferedIO` lze k enumerátoru `IOError` přistupovat přímo pomocí členských funkcí vnořených tříd `BufferedIO::BufferedInput` nebo `BufferedIO::BufferedOutput`, jak je uvedeno ve funkci `good`.  
  
> [!NOTE]
>  Vnořené třídy deklarují pouze typy v rámci oboru třídy. Nezpůsobují vytvoření obsažených objektů vnořené třídy. Předchozí příklad deklaruje dvě vnořené třídy, ale nedeklaruje žádné objekty těchto typů tříd.  
  
 Výjimka deklarace viditelnosti oboru vnořené třídy se objeví, je-li název typu deklarován spolu s dopřednou deklarací.  Název třídy, která je deklarována dopřednou deklarací, je v tomto případě viditelný mimo ohraničující třídu, kde je její obor působnosti nejmenším ohraničujícím netřídním oborem.  Příklad:  
  
```  
// nested_class_declarations_2.cpp  
class C  
{  
public:  
    typedef class U u_t; // class U visible outside class C scope  
    typedef class V {} v_t; // class V not visible outside class C  
};  
  
int main()  
{  
    // okay, forward declaration used above so file scope is used  
    U* pu;  
  
    // error, type name only exists in class C scope  
    u_t* pu2; // C2065  
  
    // error, class defined above so class C scope  
    V* pv; // C2065  
  
    // okay, fully qualified name  
    C::V* pv2;  
}  
```  
  
## <a name="access-privilege-in-nested-classes"></a>Oprávnění přístupu ve vnořených třídách  
 Vnoření třídy v rámci jiné třídy nedává zvláštní oprávnění k přístupu členským funkcím vnořené třídy. Podobně členské funkce ohraničující třídy nemají zvláštní přístup ke členům vnořené třídy.  
  
## <a name="member-functions-in-nested-classes"></a>Členské funkce ve vnořených třídách  
 Členské funkce deklarované ve vnořených třídách lze definovat v rozsahu souboru. Předchozí příklad by mohl být napsán takto:  
  
```  
// member_functions_in_nested_classes.cpp  
class BufferedIO  
{  
public:  
    enum IOError { None, Access, General };  
    class BufferedInput  
    {  
    public:  
        int read(); // Declare but do not define member  
        int good(); //  functions read and good.  
    private:  
        IOError _inputerror;  
    };  
  
    class BufferedOutput  
    {  
        // Member list.  
    };  
};  
// Define member functions read and good in  
//  file scope.  
int BufferedIO::BufferedInput::read()  
{  
   return(1);  
}  
  
int BufferedIO::BufferedInput::good()  
{  
    return _inputerror == None;  
}  
int main()  
{  
}  
```  
  
 V předchozím příkladu *kvalifikovaný název typu* syntaxe se používá k deklarovat název funkce. Deklarace:  
  
```  
BufferedIO::BufferedInput::read()  
```  
  
 znamená „funkce `read`, která je členem třídy `BufferedInput`, jež se nachází v oboru třídy `BufferedIO`“. Protože používá toto prohlášení *kvalifikovaný název typu* syntaxe, je možné konstrukce v následujícím formátu:  
  
```  
typedef BufferedIO::BufferedInput BIO_INPUT;  
  
int BIO_INPUT::read()  
```  
  
 Předchozí deklarace je ekvivalentní předchozí, ale místo názvu třídy používá název `typedef`.  
  
## <a name="friend-functions-in-nested-classes"></a>Friend – funkce ve vnořených třídách  
 Spřátelené funkce deklarované ve vnořené třídě jsou považovány za funkce v rozsahu vnořené třídy, nikoli nadřazené třídy. Proto spřátelené funkce nezískají žádná zvláštní přístupová oprávnění ke členům nebo členským funkcím nadřazené třídy. Pokud chcete použít název, který je deklarován ve vnořené třídě ve spřátelené funkci, a tato spřátelená funkce je v rozsahu souboru, použijte kvalifikované názvy typů takto:  
  
```  
// friend_functions_and_nested_classes.cpp  
  
#include <string.h>  
  
enum  
{  
    sizeOfMessage = 255  
};  
  
char *rgszMessage[sizeOfMessage];  
  
class BufferedIO  
{  
public:  
    class BufferedInput  
    {  
    public:  
        friend int GetExtendedErrorStatus();  
        static char *message;  
        static int  messageSize;  
        int iMsgNo;  
   };  
};  
  
char *BufferedIO::BufferedInput::message;  
int BufferedIO::BufferedInput::messageSize;  
  
int GetExtendedErrorStatus()  
{  
    int iMsgNo = 1; // assign arbitrary value as message number  
  
    strcpy_s( BufferedIO::BufferedInput::message,  
              BufferedIO::BufferedInput::messageSize,  
              rgszMessage[iMsgNo] );  
  
    return iMsgNo;  
}  
  
int main()  
{  
}  
```  
  
 Následující kód ukazuje funkci `GetExtendedErrorStatus` deklarovanou jako spřátelená funkce. Ve funkci, která je definována v rozsahu souboru, je zpráva zkopírována ze statického pole do člena třídy. Lepší implementace funkce `GetExtendedErrorStatus` je deklarována jako:  
  
```  
int GetExtendedErrorStatus( char *message )  
```  
  
 S předchozím rozhraním může několik tříd použít služby této funkce pomocí předání paměťového umístění, kam chtějí zkopírovat chybovou zprávu.  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)