---
title: Pole parametrů a tlačítko se třemi tečkami | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2caf6415fdbceb506b736e209c6e7e384b567c5a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384374"
---
# <a name="param-array-and-ellipsis"></a>Pole parametrů a tlačítko se třemi tečkami

Prioritou pole parametrů pro vyřešení volání přetížené funkce byl změněn z spravovaných rozšíření jazyka C++ na Visual C++.

Ve spravovaných rozšíření a nové syntaxe neexistuje žádná explicitní podpora pro pole parametrů, které podporují C# a Visual Basic. Místo toho jeden příznaky běžné pole s atributem, následujícím způsobem:

```
void Trace1( String* format, [ParamArray]Object* args[] );
void Trace2( String* format, Object* args[] );
```

Přestože obě vypadají stejně, `ParamArray` atribut to značky pro C# nebo jiných jazycích CLR jako pole trvá proměnný počet elementů s každým vyvolání. Změny v chování aplikace mezi spravovaných rozšíření a nové syntaxe je v řešení přetížené funkce nastavit v které jedna instance deklaruje tři tečky a deklaruje sekundy `ParamArray` atributů, jako v následujícím příkladu poskytované Artur Laksberg.

```
int fx(...); // 1
int fx( [ParamArray] Int32[] ); // 2
```

Ve spravovaných rozšíření se třemi tečkami se přednost atribut, který je přijatelné, protože atribut není formální aspekt jazyka. V nové syntaxi, ale pole parametrů se teď podporuje přímo v rámci jazyka a se klíči přiřadí prioritu na tři tečky vzhledem k tomu, že je více silného typu. Proto ve spravovaných rozšíření volání

```
fx( 1, 2 );
```

přeloží na `fx(...)` v nové syntaxi se překládá na `ParamArray` instance. Na vypnuto pravděpodobnost, že váš program chování závisí na vyvolání instance tlačítko se třemi tečkami přes u `ParamArray`, budete muset změnit podpis nebo volání.

## <a name="see-also"></a>Viz také

[Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)