---
title: chyby zabezpečení Spectre | Dokumentace Microsoftu
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a51d47764ea4515fcbc2cb3b7aa37fd341cd130e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463226"
---
# <a name="spectre"></a>chyby zabezpečení Spectre

**Specifické pro Microsoft**

Přikáže kompilátoru Nevkládat chyby zabezpečení Spectre variant 1 spekulativního spouštění barrier pokyny pro funkci.

## <a name="syntax"></a>Syntaxe

> **__declspec (spectre(nomitigation))**  

## <a name="remarks"></a>Poznámky

[/Qspectre](../build/reference/qspectre.md) – možnost kompilátoru způsobí, že kompilátoru k vložení spekulativního spouštění barrier pokyny, pokud analýza indikuje, že existuje ohrožení zabezpečení Spectre variant 1. Konkrétní pokyny, které jsou emitovány závisí na procesoru. I když tyto pokyny byste má minimální dopad na výkon nebo velikost kódu, můžou nastat případy, kdy kód nemá vliv ohrožení zabezpečení a vyžaduje maximální výkon.

Expertní analýzy může určit vad jednorázové přihlášení k vrácení chyby zabezpečení Spectre variant 1 hranice zabezpečení funkce před. V takovém případě lze potlačit generování kódu omezení rizik v rámci funkce použitím `__declspec(spectre(nomitigation))` k deklaraci funkce.

> [!CAUTION]
> **/Qspectre** spekulativního spouštění barrier pokyny poskytují důležitou ochranu zabezpečení a mají zanedbatelný vliv na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak používat `__declspec(spectre(nomitigation))`.

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:
 [__declspec](../cpp/declspec.md)  
 [Klíčová slova](../cpp/keywords-cpp.md)  
 [/Qspectre](../build/reference/qspectre.md)  
