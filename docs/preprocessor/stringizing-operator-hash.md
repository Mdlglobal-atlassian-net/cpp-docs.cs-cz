---
title: Nastavení velikosti řetězce (#) – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bbb1aa7db586a4b45084883491c8869b434eb8b
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466305"
---
# <a name="stringizing-operator-"></a>Operátor nastavení velikosti řetězce (#)
Znak čísla neboli operátor "převodu na řetězec" (**#**) převede parametry maker na řetězcové literály bez rozvíjení definice parametru. Používá se pouze spolu s makry, která přijímají argumenty. Je-li operátor uveden v definici makra před formálním parametrem, je skutečný argument předaný voláním makra uzavřen do uvozovek a považován za řetězcový literál. Řetězcový literál pak nahradí všechny výskyty kombinace operátoru převodu na řetězec a formálního parametru v definici makra.  
  
> [!NOTE]
> Rozšíření standardu ANSI jazyka C společností Microsoft (verze 6.0 a starší), ve kterém byly dříve rozvíjeny formální argumenty maker uvnitř řetězcových literálů a znakových konstant, již není podporováno. Kód opírající se o toto rozšíření by měl být přepsán pomocí převodu na řetězec (**#**) – operátor.  
  
Prázdný znak před prvním a za posledním tokenem skutečného argumentu je ignorován. Všechny prázdné znaky mezi tokeny ve skutečném argumentu jsou ve výsledném řetězcovém literálu redukovány na jediný prázdný znak. Proto vyskytne-li se mezi dvěma tokeny ve skutečném argumentu komentář, je redukován na jediný prázdný znak. K výslednému řetězcovému literálu jsou automaticky připojeny všechny sousedící řetězcové literály, od nichž je výsledný literál oddělen pouze prázdnými znaky.  
  
Dále, pokud znak obsažený v argumentu, obvykle vyžaduje řídicí sekvenci při použití v řetězcovém literálu (například znak uvozovek (**"**) nebo zpětné lomítko (**\\**) znaků), potřebné zpětné lomítko před něj vloženo automaticky znak.  
  
Operátor převodu na řetězec jazyka Visual C++ nechoval správně při použití s řetězci, které zahrnují řídicí sekvence. V takovém případě kompilátor generuje [Chyba kompilátoru C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md).  
  
## <a name="examples"></a>Příklady  

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