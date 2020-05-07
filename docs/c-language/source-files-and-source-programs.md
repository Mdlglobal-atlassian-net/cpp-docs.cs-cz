---
title: Zdrojové soubory a zdrojové programy
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: ac906925be551c6ee4da08e200d4028047b3d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349879"
---
# <a name="source-files-and-source-programs"></a>Zdrojové soubory a zdrojové programy

Zdrojový program lze rozdělit do jednoho nebo více „zdrojových souborů“, tzv. „jednotek převodu“. Vstup kompilátoru se nazývá „jednotka převodu“.

## <a name="syntax"></a>Syntaxe

*jednotka překladu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Externí deklarace* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*externí deklarace* *jednotky překladu*

*externí deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*definice funkce*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*změny*

[Přehled deklarací](../c-language/overview-of-declarations.md) poskytuje syntaxi pro `declaration` neterminál a *odkaz preprocesoru* vysvětluje, jak je [jednotka překladu](../preprocessor/phases-of-translation.md) zpracována.

> [!NOTE]
> Vysvětlení konvencí syntaxe standardu ANSI naleznete v úvodu do [souhrnu syntaxe jazyka C](../c-language/c-language-syntax-summary.md).

Součásti jednotky převodu jsou externí deklarace obsahující definice funkcí a deklarace identifikátorů. Tyto deklarace a definice mohou být umístěny ve zdrojových souborech, v souborech hlaviček, v knihovnách i v jiných souborech, které program potřebuje. Pro sestavení programu je zapotřebí každou jednotku převodu zkompilovat a propojit výsledné soubory objektů.

„Zdrojový program“ jazyka C je kolekcí obecných direktiv, direktiv pragma, deklarací, definicí, bloků příkazů a funkcí. Aby tyto položky byly platnými komponentami programu jazyka Microsoft C, musí být každá z nich zapsána syntaxí popsanou v této knize, přestože se mohou v programu vyskytovat v libovolném pořadí (dle pravidel uvedených v této knize). Umístění těchto komponent v programu ovlivňuje, jak v programu mohou být používány proměnné a funkce. (Další informace naleznete v tématu [Doba života, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) .)

Zdrojové soubory nemusí obsahovat spustitelné příkazy. Může být například užitečné umístit definice proměnných do jednoho zdrojového souboru, a potom deklarovat reference na tyto proměnné v jiných zdrojových souborech, které je používají. Tato technika usnadňuje hledání a v případě potřeby také aktualizace definic. Ze stejného důvodu jsou konstanty a makra často uspořádány do samostatných souborů zvaných „vložené soubory“ nebo „soubory hlaviček“, na které lze dle potřeby odkázat ve zdrojových souborech. Informace o [makrech](../preprocessor/macros-c-cpp.md) a [vložených souborech](../preprocessor/hash-include-directive-c-cpp.md)naleznete v tématu *reference preprocesoru* .

## <a name="see-also"></a>Viz také

[Struktura programu](../c-language/program-structure.md)
