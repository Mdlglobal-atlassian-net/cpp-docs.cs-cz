---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: bc4736ce233ce026ecab9ef38ac8379466b5a0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365588"
---
# <a name="safebuffers"></a>safebuffers

**Specifické pro Microsoft**

Přikáže kompilátoru nevkládat pro funkci kontroly zabezpečení přetečení vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Poznámky

Možnost kompilátoru **/GS** způsobí, že kompilátor otestuje přetečení vyrovnávací paměti vložením kontrol zabezpečení do zásobníku. Typy datových struktur, které jsou způsobilé pro kontroly zabezpečení, jsou popsány v [/GS (Buffer Security Check)](../build/reference/gs-buffer-security-check.md). Další informace o zjišťování přetečení vyrovnávací paměti naleznete [v tématu Funkce zabezpečení v msvc](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Zabezpečení funkce před přetečením vyrovnávací paměti může být určeno expertní ruční revizí kódu nebo externí analýzou. V takovém případě můžete potlačit kontroly zabezpečení funkce použitím klíčového slova **__declspec (safebuffers)** na deklaraci funkce.

> [!CAUTION]
> Kontroly zabezpečení vyrovnávací paměti poskytují důležitou ochranu zabezpečení a mají zanedbatelný vliv na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.

## <a name="inline-functions"></a>Vložené funkce

*Primární funkce* může použít klíčové slovo [vkládání](inline-functions-cpp.md) k vložení kopie *sekundární funkce*. Pokud je na funkci použito klíčové slovo **__declspec (safebuffers),** je pro tuto funkci potlačena detekce přetečení vyrovnávací paměti. Vkládání však ovlivňuje klíčové slovo **__declspec (safebuffers)** následujícími způsoby.

Předpokládejme, že možnost kompilátoru **/GS** je určena pro obě funkce, ale primární funkce určuje klíčové slovo **__declspec(safebuffers).** Datové struktury v sekundární funkci umožňují její kontroly zabezpečení a funkce tyto kontroly nepotlačuje. V tomto případě:

- Zadejte klíčové slovo [__forceinline](inline-functions-cpp.md) v sekundární funkci, chcete-li kompilátor vložit tuto funkci bez ohledu na optimalizaci kompilátoru.

- Vzhledem k tomu, že sekundární funkce je způsobilá pro kontroly zabezpečení, jsou kontroly zabezpečení použity také pro primární funkci, i když určuje klíčové slovo **__declspec (safebuffers).**

## <a name="example"></a>Příklad

Následující kód ukazuje, jak používat klíčové slovo **__declspec(safebuffers).**

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

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[inline, __inline, \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
