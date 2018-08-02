---
title: safebuffers | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b41646dbde21f68c2cc23dfbcf977d9f5ad06c1e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467497"
---
# <a name="safebuffers"></a>safebuffers
**Specifické pro Microsoft**  
  
 Přikáže kompilátoru nevkládat pro funkci kontroly zabezpečení přetečení vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>Poznámky  
 **/GS** – možnost kompilátoru způsobí, že kompilátor testuje přetečení vyrovnávací paměti vložením kontrol zabezpečení do zásobníku. Typy datových struktur způsobilých ke kontrolám zabezpečení jsou popsány v [/GS (Kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md). Další informace o detekci přetečení vyrovnávací paměti naleznete v tématu [kompilátoru kontroly zabezpečení podrobně](http://go.microsoft.com/fwlink/p/?linkid=7260) na webové stránce MSDN.  
  
 Zabezpečení funkce před přetečením vyrovnávací paměti může být určeno expertní ruční revizí kódu nebo externí analýzou. V takovém případě lze potlačit kontroly zabezpečení pro funkci s použitím **__declspec(safebuffers) oznamujete** – klíčové slovo k deklaraci funkce.  
  
> [!CAUTION]
>  Kontroly zabezpečení vyrovnávací paměti poskytují důležitou ochranu zabezpečení a mají zanedbatelný vliv na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.  
  
## <a name="inline-functions"></a>Vložené funkce  
 A *primární funkce* můžete použít [vkládání](inline-functions-cpp.md) – klíčové slovo k vložení kopie *sekundární funkci*. Pokud **__declspec(safebuffers) oznamujete** – klíčové slovo se použijí na funkce, je pro danou funkci potlačena detekce přetečení vyrovnávací paměti. Nicméně vkládání má vliv **__declspec(safebuffers) oznamujete** – klíčové slovo následujícími způsoby.  
  
 Předpokládejme, že **/GS** – možnost kompilátoru je pro obě funkce zadána, ale primární funkce určuje **__declspec(safebuffers) oznamujete** – klíčové slovo. Datové struktury v sekundární funkci umožňují její kontroly zabezpečení a funkce tyto kontroly nepotlačuje. V tomto případě:  
  
-   Zadejte [__forceinline](inline-functions-cpp.md) – klíčové slovo pro sekundární funkci a vynuťte tak vložení této funkce bez ohledu na to optimalizace kompilátoru.  
  
-   Vzhledem k tomu, že je sekundární funkce způsobilá ke kontrolám, zabezpečení platí kontroly také pro primární funkci i v případě, že se určuje **__declspec(safebuffers) oznamujete** – klíčové slovo.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje způsob použití **__declspec(safebuffers) oznamujete** – klíčové slovo.  
  
```cpp 
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
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [inline, __inline, \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)