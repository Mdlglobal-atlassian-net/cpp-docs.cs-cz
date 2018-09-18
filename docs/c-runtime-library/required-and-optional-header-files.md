---
title: Povinné a nepovinné hlavičkové soubory | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.headers
dev_langs:
- C++
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: afd523bad5d70cdfc80a6e8a532b2409be535c6b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091865"
---
# <a name="required-and-optional-header-files"></a>Povinné a nepovinné hlavičkové soubory

Popis každou rutinu runtime obsahuje seznam povinných a volitelných zahrnout, nebo záhlaví (. H), soubory pro tuto rutinu. Soubory požadované záhlaví musí být k získání deklarace funkce pro rutiny nebo jiné rutina volá se interně používá definici. Nepovinné hlavičkové soubory jsou obvykle součástí výhod předdefinovaných konstant, definic typů a vložených makra. Následující tabulka uvádí příklady obsahu souboru volitelné hlavičky:

|Definice|Příklad|
|----------------|-------------|
|Definice makra|Pokud rutina knihovny je implementovaná jako makra, může být definici makra v hlavičkovém souboru než hlavičkový soubor pro původní rutinu. Například `_toupper` makro je definováno v souboru hlaviček CTYPE. H, při funkce `toupper` je deklarován v STDLIB. H.|
|Předdefinované – konstanta|Mnoho rutin knihovny odkazují na konstanty, které jsou definovány v souborech hlaviček. Například `_open` rutina používá jako konstanty `_O_CREAT`, která je definována v hlavičkovém souboru FCNTL. H.|
|Definice typu|Některé rutiny knihoven vrátí strukturu nebo použijte k vytvoření struktury jako argument. Například vstupní a výstupní rutiny datového proudu použijte strukturu typu `FILE`, který je definován v STDIO. H.|

Soubory hlaviček knihovny run-time poskytovat deklarace funkcí ve standardní doporučené stylu ANSI/ISO C. Kompilátor provede kontrolu na rutinní odkaz, ke které dojde po její deklaraci související funkce. Deklarace funkcí jsou obzvláště důležité pro rutiny, které vracejí hodnotu typu jiného než `int`, což je výchozí hodnota. Postupy, které není zadán odpovídající vrátit hodnotu v jeho deklaraci bude považovat za kompilátorem se vraťte `int`, což může vést k neočekávaným výsledkům. Zobrazit [kontroly typu](../c-runtime-library/type-checking-crt.md) Další informace.

## <a name="see-also"></a>Viz také

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)