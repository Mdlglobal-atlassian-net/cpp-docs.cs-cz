---
title: Včetně názvů souboru v uvozovkách | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3e865df95d92dcad6b414da11677b5212e9a9f3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109935"
---
# <a name="including-quoted-filenames"></a>Zahrnutí názvů souboru v uvozovkách

**ANSI 3.8.2** podpora pro názvy v uvozovkách u zahrnutelných zdrojových souborů

Pokud zadáte jednoznačnou kompletní specifikaci cesty k souboru zahrnutí mezi dvě sady dvojitých uvozovek (" "), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.

Při zahrnutí souborů zadaných jako [#include](../preprocessor/hash-include-directive-c-cpp.md) "path-spec" hledání začne s adresářem nadřazeného souboru a pak pokračuje přes adresáře všech souborů výše nadřazených. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdrojový soubor, který se právě zpracovává. Pokud není žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání pokračuje, jako by název souboru byl uzavřen do lomených závorek.

## <a name="see-also"></a>Viz také

[Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)