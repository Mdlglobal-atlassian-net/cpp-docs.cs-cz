---
title: Zahrnutí názvů souboru v uvozovkách
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: 4083519d6f6b9b4d037b0c2998737f3a5062c6cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232953"
---
# <a name="including-quoted-filenames"></a>Zahrnutí názvů souboru v uvozovkách

**ANSI 3.8.2** podpora pro názvy v uvozovkách u zahrnutelných zdrojových souborů

Pokud zadáte jednoznačnou kompletní specifikaci cesty k souboru zahrnutí mezi dvě sady dvojitých uvozovek (" "), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.

Při zahrnutí souborů zadaných jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec" hledání začne s adresářem nadřazeného souboru a pak pokračuje přes adresáře všech souborů výše nadřazených. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdrojový soubor, který se právě zpracovává. Pokud není žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání pokračuje, jako by název souboru byl uzavřen do lomených závorek.

## <a name="see-also"></a>Viz také:

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)
