---
title: Změny v pořadí inicializace konstruktoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd54e9810131f3ddfabe458c70ddef081568a9cd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397686"
---
# <a name="changes-in-constructor-initialization-order"></a>Změny v pořadí inicializace konstruktoru

Pořadí inicializace pro třídy konstruktory změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

## <a name="comparison-of-constructor-initialization-order"></a>Porovnání pořadí inicializace konstruktoru

V rámci spravovaného rozšíření jazyka C++ inicializace konstruktoru došlo k chybě v následujícím pořadí:

1. Konstruktor základní třídy, pokud existuje, je vyvolána.

1. Inicializační seznam třídě je vyhodnocena.

1. Je proveden kód těla konstruktoru třídy.

Toto pořadí provádění se řídí stejnou konvencí jako v programování v nativním C++. Nový jazyk Visual C++ předepisuje následující pořadí zpracování pro tříd CLR:

1. Inicializační seznam třídě je vyhodnocena.

1. Konstruktor základní třídy, pokud existuje, je vyvolána.

1. Je proveden kód těla konstruktoru třídy.

Všimněte si, že tato změna se vztahuje pouze na třídy modulu CLR; nativních tříd v jazyce Visual C++ stále předchozí konvence. V obou případech tato pravidla Kaskádově přenést směrem nahoru v celém řetězu celou hierarchii z dané třídy.

Vezměte v úvahu následující příklad kódu pomocí spravovaného rozšíření jazyka C++:

```
__gc class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

__gc class B : public A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

Následující pořadí inicializace konstruktoru předepsané výše, bychom měli vidět následující pořadí provádění při nové instance třídy `B` jsou vytvořeny:

1. Konstruktor základní třídy `A` je vyvolána. `_n` Člen je inicializovaný `1`.

1. Inicializace seznamu pro třídu `B` vyhodnocena. `_m` Člen je inicializovaný `1`.

1. Kód těla třídy `B` provádí.

Teď se podíváme stejný kód v nové syntaxi jazyka Visual C++:

```
ref class A
{
public:
   A() : _n(1)
   {
   }

protected:
   int _n;
};

ref class B : A
{
public:
   B() : _m(_n)
   {
   }
private:
   int _m;
};
```

Pořadí provádění, když nové instance třídy `B` jsou vytvořeny v rámci nové syntaxe je:

1. Inicializace seznamu pro třídu `B` vyhodnocena. `_m` Člen je inicializovaný `0` (`0` je hodnota neinicializovaného `_m` člena třídy).

1. Konstruktor základní třídy `A` je vyvolána. `_n` Člen je inicializovaný `1`.

1. Kód těla třídy `B` provádí.

Všimněte si, že podobná syntaxe vrací různé výsledky pro tyto příklady kódu. Konstruktor třídy `B` závisí na hodnotě ze základní třídy `A` inicializovat jeho členů. Ale konstruktor pro třídu `A` ještě nebyla vyvolána. Tato závislost může být nebezpečné, zejména pokud zděděné třídy závisí přidělování paměti nebo prostředků vyskytuje v konstruktoru základní třídy.

## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>Co to znamená přechod ze spravovaného rozšíření jazyka C++ pro Visual C++ 2010

V mnoha případech by mělo být změny pořadí spuštění konstruktor třídy transparentní na programátorovi, protože základní třídy mít potuchy o chování zděděné třídy. Ale jak ukazují tyto příklady kódu, konstruktory zděděné třídy může se výrazně ovlivnil při jejich inicializační seznamy závisí na hodnotách členy základní třídy. Pokud přesunete kód ze spravovaných rozšíření jazyka C++ novou syntaxi, zvažte přesunutí těchto konstrukcí do těla konstruktoru třídy, kde je zaručeno objevit jako poslední spuštění.

## <a name="see-also"></a>Viz také

[Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Konstruktory](../cpp/constructors-cpp.md)
