---
title: safebuffers | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: safebuffers_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 201d4a6493b71a78f2a438ac43c003a8b7d36ce7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="safebuffers"></a>safebuffers
**Konkrétní Microsoft**  
  
 Přikáže kompilátoru nevkládat pro funkci kontroly zabezpečení přetečení vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GS** – možnost kompilátoru způsobí, že kompilátor vyzkoušet přetečení vyrovnávací paměti vložením kontrol zabezpečení v zásobníku. Typy datové struktury, které jsou způsobilé pro kontrol zabezpečení jsou popsané v [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md). Další informace o zjišťování přetečení vyrovnávací paměti najdete v tématu [kompilátoru zabezpečení kontroluje v hloubka](http://go.microsoft.com/fwlink/?linkid=7260) na webu MSDN.  
  
 Zabezpečení funkce před přetečením vyrovnávací paměti může být určeno expertní ruční revizí kódu nebo externí analýzou. V takovém případě můžete potlačit kontrol zabezpečení pro funkci s použitím `__declspec(safebuffers)` – klíčové slovo do deklarace funkce.  
  
> [!CAUTION]
>  Kontroly zabezpečení vyrovnávací paměti poskytují důležitou ochranu zabezpečení a mají zanedbatelný vliv na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.  
  
## <a name="inline-functions"></a>Vložené funkce  
 A *primární funkce* můžete použít [vložené](inline-functions-cpp.md) – klíčové slovo vložit kopii *sekundární funkce*. Pokud `__declspec(safebuffers)` – klíčové slovo, které se použijí na funkce, detekce přetečení vyrovnávací paměti je potlačeno pro tuto funkci. Ale vložené má vliv `__declspec(safebuffers)` – klíčové slovo následujícím způsobem.  
  
 Předpokládejme, že **/GS** – možnost kompilátoru je zadán pro obě funkce, ale primární funkce určuje `__declspec(safebuffers)` – klíčové slovo. Datové struktury v sekundární funkci umožňují její kontroly zabezpečení a funkce tyto kontroly nepotlačuje. V tomto případě:  
  
-   Zadejte [__forceinline](inline-functions-cpp.md) – klíčové slovo na funkci sekundární vynutit kompilátor vložené, který fungovat bez ohledu na to, optimalizace kompilátoru.  
  
-   Protože sekundární funkce nárok kontrol zabezpečení, kontrol zabezpečení, použijí se primární funkce Přestože Určuje `__declspec(safebuffers)` – klíčové slovo.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití `__declspec(safebuffers)` – klíčové slovo.  
  
```  
// compile with: /c /GS  
typedef struct {  
    int x[20];  
} BUFFER;  
static int checkBuffers() {  
    BUFFER cb;  
    // Use the buffer...  
    return 0;  
};  
static __declspec(safebuffers)   
    int noCheckBuffers() {  
    BUFFER ncb;  
    // Use the buffer...  
    return 0;  
}  
int wmain() {  
    checkBuffers();  
    noCheckBuffers();  
    return 0;  
}  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [vložené, __inline, \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check –](../preprocessor/strict-gs-check.md)