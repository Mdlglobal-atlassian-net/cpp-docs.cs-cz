---
title: spektrum | Microsoft Docs
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
ms.openlocfilehash: 153ff690b975ecb442c260fcebce73acd32d03fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422407"
---
# <a name="spectre"></a>spektrum

**Konkrétní Microsoft**

Určuje, kompilátor není vložit spektrum variant 1 spekulativní provádění bariéry pokyny pro funkci.

## <a name="syntax"></a>Syntaxe

> **__declspec (spectre(nomitigation))**  

## <a name="remarks"></a>Poznámky

[/Qspectre](../build/reference/qspectre.md) – možnost kompilátoru způsobí, že kompilátor vložte pokyny bariéry spekulativní provádění kde analýza indikuje, že existuje chyba zabezpečení spektrum variant 1. Konkrétní pokyny vygenerované závisí na procesor. Pokud tyto pokyny musí mít minimální dopad na výkon nebo velikosti kódu, může být případy, kdy váš kód nemá vliv ohrožení zabezpečení a vyžaduje maximální výkon.

Odborné analysis může určit, že funkce je bezpečné z vadu spektrum variant 1 rozsah kontroly jednorázové přihlášení. V takovém případě můžete potlačit generování kódu zmírnění v rámci funkce použitím `__declspec(spectre(nomitigation))` do deklarace funkce.

> [!CAUTION]
> **/Qspectre** spekulativní provádění bariéry pokyny poskytují ochranu důležité zabezpečení a mít nepatrné dopad na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.

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

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)  
[Klíčová slova](../cpp/keywords-cpp.md)  
[/Qspectre](../build/reference/qspectre.md)  
