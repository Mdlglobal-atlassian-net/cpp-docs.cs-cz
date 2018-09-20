---
title: C + +/ CLI Základy migrace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88b32ea226971c0fa5b6d269a8992629c3c4de77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385428"
---
# <a name="ccli-migration-primer"></a>Základy migrace v jazyku C++/CLI

Toto je průvodce přesunem vašich programů aplikace Visual C++ ze spravovaného rozšíření jazyka C++ pro Visual C++.

C + +/ CLI rozšiřuje dynamickou komponentu programovacího paradigmatu na standardní jazyk ISO-C++. Nový jazyk nabízí řadu významných vylepšení oproti spravovaným rozšířením. Tato část obsahuje výčtový seznam spravovaného rozšíření funkcí jazyka C++ a jejich mapování na Visual C++, pokud takové mapování existuje a poukazuje na ty konstrukce, pro které neexistuje žádné mapování.

## <a name="in-this-section"></a>V tomto oddílu

[Přehled změn (C++/CLI)](../dotnet/outline-of-changes-cpp-cli.md)<br/>
Vysoká úroveň osnovy rychlého odkazu, která poskytuje seznam výčtu změn v pěti základních kategoriích.

[Klíčová slova jazyka (C++/CLI)](../dotnet/language-keywords-cpp-cli.md)<br/>
Tento článek popisuje změny v klíčových slovech jazyka, včetně odstranění dvojitého podtržítka a zavedení kontextu a oddělení klíčových slov.

[Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
Přihlíží k syntaktickým změnám v deklaraci z běžných typ systému (CTS) – to zahrnuje i změny v deklaraci tříd, polí (zahrnuje parametr pole), výčtů a tak dále.

[Deklarace členů v rámci třídy nebo rozhraní (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
Uvádí změny zahrnující třídní členy jako jsou Skalární vlastnosti, vlastnosti indexu, operátory, delegáti a události.

[Hodnotové typy a jejich chování (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
Zaměřuje se na typy hodnot a na novou řadu vnitřních a přídavných ukazatelů. Také popisuje několik významných sémantických změn, jako je například zavedení implicitního zabalení, neměnitelnosti zabalených typových hodnot a odstranění podpory pro výchozí konstruktory hodnoty tříd.

[Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
Podrobně popisuje sémantické změny, jako je například podpora zápisu přetypování, řetězcový literál chování a změny v sémantice mezi standardem ISO-C++ a C + +/ CLI.

## <a name="see-also"></a>Viz také

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)