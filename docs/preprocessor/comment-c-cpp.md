---
title: comment – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 3175ad5318bcc6fd9aa6233258ccec9033c89be8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219097"
---
# <a name="comment-pragma"></a>comment – direktiva pragma

Umístí záznam komentáře do souboru objektu nebo do spustitelného souboru.

## <a name="syntax"></a>Syntaxe

> **#pragma komentář (** *komentář-typ* [ **,** "*Komentář-řetězec*"] **)**

## <a name="remarks"></a>Poznámky

*Typ komentáře* je jeden z předdefinovaných identifikátorů popsaných níže, který určuje typ záznamu komentáře. Volitelný *řetězec komentáře* je řetězcový literál, který poskytuje další informace pro některé typy komentářů. Vzhledem k tomu, že *řetězec komentáře* je řetězcový literál, dodržuje všechna pravidla pro řetězcové literály s ohledem na řídicí znaky, vložené uvozovky`"`() a zřetězení.

### <a name="compiler"></a>– kompilátor

Umístí název a číslo verze kompilátoru do souboru objektu. Tento záznam komentáře se v linkeru ignoruje. Pokud zadáte parametr *řetězce komentáře* pro tento typ záznamu, kompilátor vygeneruje upozornění.

### <a name="lib"></a>Knihovna

Umístí záznam hledání knihovny do souboru objektů. K tomuto typu komentáře musí doprovázet parametr *řetězce Comment* obsahující název (a případně cestu) knihovny, kterou má linker Hledat. Název knihovny následuje po výchozí knihovně – prohledání záznamů v souboru objektů; linker vyhledá tuto knihovnu stejně, jako kdyby se na příkazovém řádku jmenovala Tato knihovna, a to za předpokladu, že knihovna není zadaná pomocí [/NODEFAULTLIB](../build/reference/nodefaultlib-ignore-libraries.md). V jednom zdrojovém souboru můžete umístit více záznamů hledání knihovny. Každý záznam se zobrazí v souboru objektu ve stejném pořadí, ve kterém byl nalezen ve zdrojovém souboru.

Pokud je důležité pořadí výchozí knihovny a přidané knihovny důležité, kompilace s přepínačem [/zl](../build/reference/zl-omit-default-library-name.md) zabrání v umístění názvu výchozí knihovny do modulu Object. Direktivu pragma druhého komentáře pak lze použít k vložení názvu výchozí knihovny po přidané knihovně. Knihovny uvedené s těmito direktivami pragma se zobrazí v modulu objektu ve stejném pořadí, ve kterém jsou nalezeny ve zdrojovém kódu.

### <a name="linker"></a>linker

Umístí [možnost linkeru](../build/reference/linker-options.md) do souboru objektu. Pomocí tohoto typu komentáře můžete zadat možnost linkeru místo předání do příkazového řádku nebo jeho zadání ve vývojovém prostředí. Například můžete zadat možnost/include pro vynucení zahrnutí symbolu:

```C
#pragma comment(linker, "/include:__mySymbol")
```

Pouze následující možnosti linkeru (*typ komentář*) jsou k dispozici pro předání do identifikátoru linkeru:

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>uživatel

Umístí obecný komentář do souboru objektu. Parametr *řetězce komentáře* obsahuje text komentáře. Tento záznam komentáře se v linkeru ignoruje.

## <a name="examples"></a>Příklady

Následující direktiva pragma způsobí, že linker vyhledá EMAPI. Knihovna LIB při propojování Linker nejdříve vyhledá v aktuálním pracovním adresáři a pak v cestě zadané v proměnné prostředí LIB.

```C
#pragma comment( lib, "emapi" )
```

Následující direktiva pragma způsobí, že kompilátor umístí do souboru objektu název a číslo verze kompilátoru:

```C
#pragma comment( compiler )
```

Pro komentáře, které přijímají parametr *řetězce Comment* , můžete použít makro na jakémkoli místě, kde byste použili řetězcový literál, za předpokladu, že se makro rozšíří na řetězcový literál. Můžete také zřetězit libovolnou kombinaci řetězcových literálů a makra, která se rozšiřují na řetězcové literály. Například následující příkaz je přijatelný:

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
