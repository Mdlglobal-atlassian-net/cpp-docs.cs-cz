---
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 40eee25dec867ae3fce7a6b2d4715f0be81bfe76
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926372"
---
# <a name="spectre"></a>spectre

**Specifické pro společnost Microsoft**

Instruuje kompilátor, aby nevložil Spectre variantu spekulativních funkcí bariéry k provedení.

## <a name="syntax"></a>Syntaxe

> **__declspec (Spectre (nezmírňování))**

## <a name="remarks"></a>Poznámky

Možnost kompilátoru [/Qspectre](../build/reference/qspectre.md) způsobí, že kompilátor vloží pokyny k spekulativním bariérám při spuštění. Jsou vloženy tam, kde analýza indikuje, že existuje zranitelnost zabezpečení Spectre varianty 1. Konkrétní pokyny, které byly vygenerovány, závisí na procesoru. I když by tyto pokyny měly mít minimální dopad na velikost nebo výkon kódu, mohou nastat případy, kdy váš kód není ovlivněn ohrožením zabezpečení a vyžaduje maximální výkon.

Odborník na analýzu může určit, že funkce je bezpečná, z Spectre variant s 1 variantou check. V takovém případě můžete potlačit generování rizikového kódu ve funkci `__declspec(spectre(nomitigation))` použitím deklarace funkce.

> [!CAUTION]
> Pokyny pro **/Qspectre** spekulativních operací proti spuštění poskytují důležitou ochranu zabezpečení a mají zanedbatelný dopad na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.

## <a name="example"></a>Příklad

Následující kód ukazuje, jak použít `__declspec(spectre(nomitigation))`.

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
