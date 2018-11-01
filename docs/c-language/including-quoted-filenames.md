---
title: Zahrnutí názvů souboru v uvozovkách
ms.date: 11/04/2016
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
ms.openlocfilehash: 11beaa3a91f476348c57b12ab3febad7cb9c89fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656713"
---
# <a name="including-quoted-filenames"></a>Zahrnutí názvů souboru v uvozovkách

**ANSI 3.8.2** podpora pro názvy v uvozovkách u zahrnutelných zdrojových souborů

Pokud zadáte jednoznačnou kompletní specifikaci cesty k souboru zahrnutí mezi dvě sady dvojitých uvozovek (" "), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.

Při zahrnutí souborů zadaných jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec" hledání začne s adresářem nadřazeného souboru a pak pokračuje přes adresáře všech souborů výše nadřazených. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdrojový soubor, který se právě zpracovává. Pokud není žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání pokračuje, jako by název souboru byl uzavřen do lomených závorek.

## <a name="see-also"></a>Viz také

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)