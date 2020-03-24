---
title: Chyba kompilátoru C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 93b6e414f26c56702a1c7ac12863cbcd5063b570
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177492"
---
# <a name="compiler-error-c2558"></a>Chyba kompilátoru C2558

Identifikátor: není k dispozici konstruktor kopie nebo je konstruktor kopie deklarován explicitně

Konstruktor kopie inicializuje objekt z jiného objektu stejného typu. (Vytvoří kopii objektu.) Kompilátor vygeneruje výchozí kopírovací konstruktor, pokud nedefinujete žádné konstruktory.

### <a name="to-fix-this-error"></a>Odstranění této chyby

1. K tomuto problému může dojít, když se provede pokus o zkopírování třídy, jejíž kopírovací konstruktor je `private`. Ve většině případů nesmí být kopírována třída, která má kopírovací konstruktor `private`. Společná programovací technika deklaruje konstruktor kopírování `private`, aby se zabránilo přímému použití třídy. Tato třída může být sama o sobě nepoužitelná nebo ke správné funkci vyžaduje jinou třídu.

   Pokud zjistíte, že je bezpečné použít třídu, která má konstruktor kopírování `private`, odvodit novou třídu z třídy, která má konstruktor `private` a vytvořte `public` nebo `protected` kopírovací konstruktor, který je k dispozici v nové třídě. Použijte odvozenou třídu namísto původní.

1. K tomuto problému může dojít, když se provede pokus o zkopírování třídy, jejíž kopírovací konstruktor je explicitní. Deklarace kopírovacího konstruktoru jako `explicit` zabraňuje předávání nebo vracení objektů třídy do funkcí nebo z nich. Další informace o explicitních konstruktorech naleznete v tématu [uživatelsky definované převody typů](../../cpp/user-defined-type-conversions-cpp.md).

1. K tomuto problému může dojít, když se provede pokus o zkopírování instance třídy deklarované `const` pomocí kopírovacího konstruktoru, který nepřijímá parametr `const` odkazu. Deklarace kopírovacího konstruktoru s odkazem na typ `const` namísto odkaz na typ, který není const.
