---
title: "Nastavení velikosti řetězce (#) – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 585bdd0fa11cecdf3fb337f8c11d2287fe495371
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="stringizing-operator-"></a>Operátor nastavení velikosti řetězce (#)
Počet přihlášení nebo operátor "nastavení velikosti řetězce" (**#**) převede parametrů maker na textové literály bez rozbalení definici parametru. Používá se pouze spolu s makry, která přijímají argumenty. Je-li operátor uveden v definici makra před formálním parametrem, je skutečný argument předaný voláním makra uzavřen do uvozovek a považován za řetězcový literál. Řetězcový literál pak nahradí všechny výskyty kombinace operátoru převodu na řetězec a formálního parametru v definici makra.  
  
> [!NOTE]
>  Rozšíření standardu ANSI jazyka C společností Microsoft (verze 6.0 a starší), ve kterém byly dříve rozvíjeny formální argumenty maker uvnitř řetězcových literálů a znakových konstant, již není podporováno. Kód, který spoléhali na toto rozšíření by měl být přepsána pomocí nastavení velikosti řetězce (**#**) operátor.  
  
Prázdný znak před prvním a za posledním tokenem skutečného argumentu je ignorován. Všechny prázdné znaky mezi tokeny ve skutečném argumentu jsou ve výsledném řetězcovém literálu redukovány na jediný prázdný znak. Proto vyskytne-li se mezi dvěma tokeny ve skutečném argumentu komentář, je redukován na jediný prázdný znak. K výslednému řetězcovému literálu jsou automaticky připojeny všechny sousedící řetězcové literály, od nichž je výsledný literál oddělen pouze prázdnými znaky.  
  
Další, pokud znak obsažené v argumentu obvykle vyžaduje, aby v řídicí sekvenci při použití v řetězcový literál (například uvozovky (**"**) nebo zpětné lomítko (**\\**) znaků), zpětné lomítko nezbytné řídicí automaticky vložen před znak.  
  
Operátor stringizing Visual C++ není chovat správně při použití s řetězců, které obsahují řídicí sekvence. V takovém případě kompilátor vygeneruje [C2017 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2017.md).  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje definici makra obsahující operátor převodu na řetězec a hlavní funkci, která makro volá:  
  
Taková volání by byla rozvinuta během předběžného zpracování a vytvořila by následující kód:  
  
```cpp  
int main() {  
   printf_s( "In quotes in the printf function call\n" "\n" );  
   printf_s( "\"In quotes when printed to the screen\"\n" "\n" );  
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );  
}  
```  
  
```cpp  
// stringizer.cpp  
#include <stdio.h>  
#define stringer( x ) printf_s( #x "\n" )  
int main() {  
   stringer( In quotes in the printf function call );   
   stringer( "In quotes when printed to the screen" );     
   stringer( "This: \"  prints an escaped double quote" );  
}  
```  
  
```Output  
In quotes in the printf function call  
"In quotes when printed to the screen"  
"This: \"  prints an escaped double quote"  
```  
  
## <a name="example"></a>Příklad  
Následující příklad ukazuje, jak lze rozvinout parametr makra:  
  
```cpp  
// stringizer_2.cpp  
// compile with: /E  
#define F abc  
#define B def  
#define FB(arg) #arg  
#define FB1(arg) FB(arg)  
FB(F B)  
FB1(F B)  
```  
  
## <a name="see-also"></a>Viz také  
 [Operátory preprocesoru](../preprocessor/preprocessor-operators.md)