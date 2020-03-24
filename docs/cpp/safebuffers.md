---
title: safebuffers
ms.date: 11/04/2016
f1_keywords:
- safebuffers_cpp
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
ms.openlocfilehash: 705d3eca67f87e505a147af4984496d3af43dd53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178909"
---
# <a name="safebuffers"></a>safebuffers

**Specifické pro společnost Microsoft**

Přikáže kompilátoru nevkládat pro funkci kontroly zabezpečení přetečení vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```
__declspec( safebuffers )
```

## <a name="remarks"></a>Poznámky

Možnost kompilátoru **/GS** způsobí, že kompilátor testuje přetečení vyrovnávací paměti tím, že do zásobníku vloží kontroly zabezpečení. Typy datových struktur, které mají nárok na kontroly zabezpečení, jsou popsány v tématu [/GS (kontrola zabezpečení vyrovnávací paměti)](../build/reference/gs-buffer-security-check.md). Další informace o detekci přetečení vyrovnávací paměti najdete v tématu [funkce zabezpečení v MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/06/28/security-features-in-microsoft-visual-c/).

Zabezpečení funkce před přetečením vyrovnávací paměti může být určeno expertní ruční revizí kódu nebo externí analýzou. V takovém případě můžete potlačit kontroly zabezpečení pro funkci použitím klíčového slova **__declspec (safebuffers)** pro deklaraci funkce.

> [!CAUTION]
>  Kontroly zabezpečení vyrovnávací paměti poskytují důležitou ochranu zabezpečení a mají zanedbatelný vliv na výkon. Proto je doporučeno je nepotlačovat vyjma vzácných případů, kdy je výkon funkce kriticky důležitý a funkce je známa jako bezpečná.

## <a name="inline-functions"></a>Vložené funkce

*Primární funkce* [může k vložení](inline-functions-cpp.md) kopie *sekundární funkce*použít klíčové slovo. Pokud je klíčové slovo **__declspec (safebuffers)** použito pro funkci, rozpoznávání přetečení vyrovnávací paměti je pro tuto funkci potlačeno. Vkládání však má vliv na klíčová slova **__declspec (safebuffers)** následujícími způsoby.

Předpokládejme, že je pro obě funkce zadaná možnost kompilátoru **/GS** , ale primární funkce určuje klíčové slovo **__declspec (safebuffers)** . Datové struktury v sekundární funkci umožňují její kontroly zabezpečení a funkce tyto kontroly nepotlačuje. V tomto případě:

- Zadejte klíčové slovo [__forceinline](inline-functions-cpp.md) pro sekundární funkci, aby kompilátor vynutil vložení této funkce bez ohledu na optimalizace kompilátoru.

- Vzhledem k tomu, že sekundární funkce má nárok na kontroly zabezpečení, jsou kontroly zabezpečení také aplikovány na primární funkci i v případě, že Určuje klíčové slovo **__declspec (safebuffers)** .

## <a name="example"></a>Příklad

Následující kód ukazuje použití klíčového slova **__declspec (safebuffers)** .

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[inline, __inline \__forceinline](inline-functions-cpp.md)<br/>
[strict_gs_check](../preprocessor/strict-gs-check.md)
