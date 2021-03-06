---
title: Fáze převodu
ms.date: 08/29/2019
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: d072c9aec48d815ba85f8a12576baa6447703f8c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218302"
---
# <a name="phases-of-translation"></a>Fáze převodu

Programy jazyků C a C++ se skládají z jednoho nebo více zdrojových souborů, z nichž každý obsahuje část textu programu. Zdrojový soubor společně s jeho *soubory zahrnutí*, soubory, které jsou zahrnuty pomocí `#include` direktivy preprocesoru, ale ne, včetně sekcí kódu odebraných direktivami podmíněné `#if`kompilace, jako je například, se označuje jako  *jednotka překladu*

Zdrojové soubory lze přeložit v různých časech. Ve skutečnosti je běžné překládat pouze soubory se zastaralými daty. Přeložené jednotky překladu mohou být zpracovány do souborů samostatného objektu nebo do knihoven kódu objektu. Tyto samostatné přeložené jednotky překladu jsou následně propojeny pro utvoření spustitelného programu nebo dynamické knihovny (DLL). Další informace o souborech, které lze použít jako vstup do linkeru, najdete v tématu [Propojování vstupních souborů](../build/reference/link-input-files.md).

Jednotky překladu mohou komunikovat pomocí:

- Volání funkcí, které mají vnější propojení.

- Volání funkcí členských tříd, které mají vnější propojení.

- Přímých úprav objektů, které mají vnější propojení.

- Přímých úprav souborů.

- Meziprocesové komunikace (pouze pro aplikace založené na operačním systému Microsoft Windows).

Následující seznam popisuje fáze, ve kterých kompilátor překládá soubory:

*Mapování znaků*\
Znaky jsou ve zdrojovém souboru mapovány na reprezentaci vnitřního zdroje. Sekvence trigraph jsou v této fázi převedeny na vnitřní reprezentaci jedním znakem.

*Spojení řádků*\
Všechny řádky, které končí zpětným lomítkem ( **\\** ) ihned následované znakem nového řádku, jsou spojeny s dalším řádkem ve zdrojovém souboru a tvoří logické řádky z fyzických řádků. Pokud není prázdný, musí zdrojový soubor končit znakem nového řádku, který nepředchází zpětné lomítko.

*Tokenizace*\
Zdrojový soubor je rozdělen do předzpracovaných tokenů a prázdných znaků. Komentáře ve zdrojovém souboru jsou nahrazeny každý jednou mezerou. Jsou zachovány znaky nového řádku.

*Předzpracování*\
Direktivy předběžného zpracování jsou vykonány a makra jsou rozbalena do zdrojového souboru. Příkaz `#include` vyvolá na jakémkoli textu překlad začínající od předchozích tří kroků.

*Mapování znakových sad*\
Všechny členy zdrojové znakové sady a řídicí sekvence jsou ve znakové sadě spuštění převedeny na jejich ekvivalence. U jazyků Microsoft C a C++ jsou znakové sady spuštění a zdrojové znakové sady ASCII.

*Zřetězení řetězců*\
Všechny sousední řetězce a literály širokých řetězců jsou zřetězeny. Například `"String " "concatenation"` se bude `"String concatenation"`jednat o.

*NAT*\
Všechny tokeny jsou analyzovány syntakticky a sémanticky. Tyto tokeny jsou převedeny na kód objektu.

*Vazby*\
Všechny externí odkazy jsou využity pro vytvoření spustitelného programu nebo dynamické knihovny DLL.

Kompilátor vytváří varování nebo chyby v průběhu fází překladu, ve kterých narazí na chyby syntaxe.

Linker řeší všechny externí odkazy a vytvoří spustitelný program nebo knihovnu DLL spojením jedné nebo více samostatně zpracovaných jednotek překladu spolu se standardními knihovnami.

## <a name="see-also"></a>Viz také:

[Preprocesor](../preprocessor/preprocessor.md)
