---
title: "upozornění | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- warning_CPP
- vc-pragma.warning
dev_langs: C++
helpviewer_keywords:
- pragmas, warning
- push pragma warning
- pop warning pragma
- warning pragma
ms.assetid: 8e9a0dec-e223-4657-b21d-5417ebe29cc8
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 275ca0a1101141ef1c0f4217597a644a6dbd8c46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="warning-pragma"></a>– Direktiva Pragma upozornění
Umožňuje selektivní změny chování zprávy upozornění kompilátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```
#pragma warning(   
    warning-specifier : warning-number-list [; warning-specifier : warning-number-list...] )  
#pragma warning( push[ ,n ] )  
#pragma warning( pop )  
```  
  
## <a name="remarks"></a>Poznámky  
Následující upozornění – specifikátor parametry jsou k dispozici.  
  
|upozornění – specifikátor|Význam|  
|------------------------|-------------|  
|`1, 2, 3, 4`|Použít danou úroveň u zadané upozorněními. To také zapne zadaný upozornění, které se ve výchozím nastavení.|  
|`default`|Upozornění chování resetovat na výchozí hodnotu. To také zapne zadaný upozornění, které se ve výchozím nastavení. Upozornění budou generovány v jeho výchozí, zdokumentovat, úroveň.<br /><br /> Další informace najdete v tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../preprocessor/compiler-warnings-that-are-off-by-default.md).|  
|`disable`|Příkaz zadaný zprávy upozornění.|  
|`error`|Sestavy zadaný upozornění jako chyby.|  
|`once`|Zobrazení zadané zprávy pouze jednou.|  
|`suppress`|V zásobníku nabízených oznámení aktuální stav – Direktiva pragma, zakáže zadaný upozornění pro další řádek a pak otevře zásobník upozornění tak, aby se vynuluje stav – Direktiva pragma.|  
  
 Příkaz následující kód ukazuje, že `warning-number-list` parametru může obsahovat více čísel upozornění a že více `warning-specifier` v stejné – Direktiva pragma lze zadat parametry.  
  
```cpp  
#pragma warning( disable : 4507 34; once : 4385; error : 164 )  
```  
  
 Toto je funkčně srovnatelný následující kód.  
  
```cpp  
// Disable warning messages 4507 and 4034.  
#pragma warning( disable : 4507 34 )  
  
// Issue warning 4385 only once.  
#pragma warning( once : 4385 )  
  
// Report warning 4164 as an error.  
#pragma warning( error : 164 )  
```  
  
 Kompilátor přidá 4000 na libovolné číslo upozornění, která je od 0 do 999.  
  
 Pro upozornění číslice v rozsahu 4700 4999, které jsou ty, které jsou přidružené k generování kódu, bude stav upozornění platit při kompilátor narazí otevřete složené závorky funkce platná pro zbytek funkce. Pomocí `warning` – Direktiva pragma ve funkci na změnu stavu upozornění, které se má číslo větší než 4699 se projeví až po skončení funkce. Následující příklad ukazuje správné umístění `warning` direktivy zakázat upozornění generování kódu a pak ho obnovit.  
  
```cpp  
// pragma_warning.cpp  
// compile with: /W1  
#pragma warning(disable:4700)  
void Test() {  
   int x;  
   int y = x;   // no C4700 here  
   #pragma warning(default:4700)   // C4700 enabled after Test ends  
}  
  
int main() {  
   int x;  
   int y = x;   // C4700  
}  
```  
  
 Všimněte si, že v rámci funkce textu, poslední nastavení jazyka `warning` – Direktiva pragma bude platit pro celou funkci.  
  
## <a name="push-and-pop"></a>Nabízení a Pop  
 `warning` – Direktiva pragma také podporuje syntaxi, kde `n` představuje úroveň pro upozornění (1 až 4).  
  
 `#pragma warning( push [ , n ] )`  
  
 `#pragma warning( pop )`  
   
 – Direktiva pragma `warning( push )` uloží aktuální stav varování u každé upozornění. – Direktiva pragma `warning( push, n )` ukládá aktuální stav pro každý upozornění a nastaví globální úroveň pro upozornění na `n`.  
  
 – Direktiva pragma `warning( pop )` bodů POP poslední stav upozornění vloženy do zásobníku. Veškeré změny, které jste do stavu upozornění mezi `push` a `pop` se vrátit zpět. Vezměte v úvahu v tomto příkladu:  
  
```cpp  
#pragma warning( push )  
#pragma warning( disable : 4705 )  
#pragma warning( disable : 4706 )  
#pragma warning( disable : 4707 )  
// Some code  
#pragma warning( pop )   
```  
  
 Na konci tohoto kódu `pop` obnoví stav každé varování (zahrnuje 4705, 4706 a 4707) které byly při spuštění kódu.  
  
 Když píšete soubory hlaviček, můžete použít `push` a `pop` zaručit, že stav varování změny provedené uživatelem nezabrání hlavičky kompilování správně. Použití `push` na začátku hlavičku a `pop` na konci. Například pokud máte hlavičku, která není řádně zkompilovat na úrovni upozornění 4, následující kód by změnit úroveň pro upozornění na 3 a obnovte původní úroveň pro upozornění na konci záhlaví.  
  
```cpp  
#pragma warning( push, 3 )  
// Declarations/definitions  
#pragma warning( pop )   
```  
  
 Další informace o kompilátoru možnosti, které vám pomůžou potlačení upozornění, naleznete v části [/FI](../build/reference/fi-name-forced-include-file.md) a [/w](../build/reference/compiler-option-warning-level.md).  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)