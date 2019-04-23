---
title: Fáze posunutí
ms.date: 10/18/2018
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: 11e36e06adc4fa95cb9aa607704e72f64c812429
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036150"
---
# <a name="phases-of-translation"></a>Fáze posunutí

Programy jazyků C a C++ se skládají z jednoho nebo více zdrojových souborů, z nichž každý obsahuje část textu programu. Zdrojový soubor spolu s jeho vloženými soubory (soubory, které jsou zahrnuty pomocí direktivy preprocesoru `#include`), s výjimkou částí kódu odebraných pomocí direktiv podmíněné kompilace, jako je `#if`, se nazývá „jednotka překladu“.

Zdrojové soubory lze přeložit v různých časech. Ve skutečnosti je běžné překládat pouze zastaralé soubory. Přeložené jednotky překladu mohou být zpracovány do souborů samostatného objektu nebo do knihoven kódu objektu. Tyto samostatné přeložené jednotky překladu jsou následně propojeny pro utvoření spustitelného programu nebo dynamické knihovny (DLL).  Další informace o souborech, které lze použít jako vstup do linkeru, naleznete v tématu [vstupní soubory LINK](../build/reference/link-input-files.md).

Jednotky překladu mohou komunikovat pomocí:

- Volání funkcí, které mají vnější propojení.

- Volání funkcí členských tříd, které mají vnější propojení.

- Přímých úprav objektů, které mají vnější propojení.

- Přímých úprav souborů.

- Meziprocesové komunikace (pouze pro aplikace založené na operačním systému Microsoft Windows).

Následující seznam popisuje fáze, ve kterých kompilátor překládá soubory:

*Mapování znaků*<br/>
Znaky jsou ve zdrojovém souboru mapovány na reprezentaci vnitřního zdroje. Sekvence trigraph jsou v této fázi převedeny na vnitřní reprezentaci jedním znakem.

*Spojování řádků*<br/>
Všechny řádky, které končí lomítkem (**\\**) a jsou ihned následovány znakem znak, jsou spojeny s dalším řádkem ve zdrojovém souboru, které tvoří logické řádky z fyzických řádků. Pokud není zdrojový soubor prázdný, musí končit znakem pro nový řádek, který není za znakem zpětného lomítka.

*Tokenizace*<br/>
Zdrojový soubor je rozdělen do předzpracovaných tokenů a prázdných znaků. Komentáře ve zdrojovém souboru jsou nahrazeny každý jednou mezerou. Jsou zachovány znaky nového řádku.

*Předzpracování*<br/>
Direktivy předběžného zpracování jsou vykonány a makra jsou rozbalena do zdrojového souboru. Příkaz `#include` vyvolá na jakémkoli textu překlad začínající od předchozích tří kroků.

*Mapování znakové sady*<br/>
Všechny členy zdrojové znakové sady a řídicí sekvence jsou ve znakové sadě spuštění převedeny na jejich ekvivalence. U jazyků Microsoft C a C++ jsou znakové sady spuštění a zdrojové znakové sady ASCII.

*Zřetězení řetězců*<br/>
Všechny sousední řetězce a literály širokých řetězců jsou zřetězeny. Například `"String " "concatenation"` stane `"String concatenation"`.

*Translation*<br/>
Všechny tokeny jsou analyzovány syntakticky a sémanticky. Tyto tokeny jsou převedeny na kód objektu.

*Propojení*<br/>
Všechny externí odkazy jsou využity pro vytvoření spustitelného programu nebo dynamické knihovny DLL.

Kompilátor vytváří varování nebo chyby v průběhu fází překladu, ve kterých narazí na chyby syntaxe.

Linker řeší všechny externí odkazy a vytvoří spustitelný program nebo knihovnu DLL spojením jedné nebo více samostatně zpracovaných jednotek překladu spolu se standardními knihovnami.

## <a name="see-also"></a>Viz také:

[Preprocesor](../preprocessor/preprocessor.md)