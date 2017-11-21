---
title: "C + +/ CLI migrace Úvod do | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++/CLI Version 2
- upgrading Visual C++ applications, Managed Extensions for C++ to Visual C++ 2005 syntax
- migration [C++], C++/CLI Version 2
- Managed Extensions for C++, upgrading syntax
- C++/CLI Version 2, managed extensions
ms.assetid: 8ec926b5-73f6-4f0c-bcdf-5203d293849a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5861a4931a1241a213157b94ca189c6b95f0fb6a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccli-migration-primer"></a>Základy migrace v jazyku C++/CLI
Toto je Průvodce při přechodu programy Visual C++ ze spravovaných rozšíření jazyka C++ na Visual C++. Souhrn syntaktických změn naleznete v tématu [(NOTINBUILD) spravovaných rozšíření pro C++ Syntax Upgrade Checklist](http://msdn.microsoft.com/en-us/edbded88-7ef3-4757-bd9d-b8f48ac2aada).  
  
 C + +/ CLI rozšiřuje programovací zlepší dynamické součást standardní jazyk ISO C++. Nový jazyk nabízí několik významných vylepšení oproti spravovaných rozšíření. Tato část obsahuje výčtový seznam spravovaných rozšíření funkcí jazyka C++ a jejich mapování pro aplikaci Visual C++, pokud takové mapování existuje a poukazuje těchto konstrukce, pro které neexistuje žádné mapování.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled změn (C + +/ CLI)](../dotnet/outline-of-changes-cpp-cli.md)  
 Hrubý nástin Stručná referenční příručka poskytuje seznam výčtu změn v pěti obecné kategorie.  
  
 [Klíčová slova jazyka (C + +/ CLI)](../dotnet/language-keywords-cpp-cli.md)  
 Popisuje změny v klíčová slova jazyka, včetně odebrání dvojité podtržítko a zavedení kontextu a oddělení klíčová slova.  
  
 [Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)  
 Vypadá na syntaktické změny v deklaraci z běžných typ systému (CTS) – to zahrnuje změny, v deklaraci třídy, pole (včetně pole parametrů), výčty a tak dále.  
  
 [Deklarace členů v rámci třídy nebo rozhraní (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)  
 Uvede změny zahrnující členy třídy, jako je například Skalární vlastnosti, vlastnosti index, operátory, delegáti a události.  
  
 [Hodnotové typy a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)  
 Zaměřuje se na nové řady vnitřních a přídavných ukazatelů a typů hodnot. Popisuje také počet sémantiku významné změny, jako je například zavedení implicitní zabalení, neměnitelnosti pevně určené typy hodnot a odebrání podpory pro výchozí konstruktory hodnoty tříd.  
  
 [Obecné jazykové změny (C + +/ CLI)](../dotnet/general-language-changes-cpp-cli.md)  
 Podrobnosti o sémantickými změnami, jako je podpora pro zápis přetypování řetězce literálu chování a změny v sémantice mezi ISO-C++ a C + +/ CLI.  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)   
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)