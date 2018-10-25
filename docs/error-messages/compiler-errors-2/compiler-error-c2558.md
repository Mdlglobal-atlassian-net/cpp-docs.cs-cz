---
title: Chyba kompilátoru C2558 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2558
dev_langs:
- C++
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6129bea28b943f8f18e1cf6b1e760e604223bdc1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060933"
---
# <a name="compiler-error-c2558"></a>Chyba kompilátoru C2558

Identifikátor: není k dispozici konstruktor kopie nebo je konstruktor kopie deklarován explicitně

Konstruktor kopie inicializuje objekt z jiného objektu stejného typu. (Vytvoří kopii tohoto objektu.) Pokud nedefinujete žádné konstruktory, vygeneruje kompilátor výchozí kopii.

### <a name="to-fix-this-error"></a>Odstranění této chyby

1. Tento problém může dojít, když je kopie třídy, jejíž konstruktor kopie je proveden pokus o `private`. Ve většině případů třídu, která má `private` kopírovací konstuktor neměla kopírovat. Běžně deklaruje `private` kopírovací konstruktor, aby se zabránilo přímému použití třídy. Tato třída může být sama o sobě nepoužitelná nebo ke správné funkci vyžaduje jinou třídu.

   Pokud zjistíte, že je bezpečné používat třídu, která má `private` kopírovací konstruktor, odvodit novou třídu od třídy, který má `private` a zpřístupněte `public` nebo `protected` k dispozici v této nové třídě konstruktor kopie. Použijte odvozenou třídu namísto původní.

1. Tento problém může dojít při pokusu o kopie třídy, jejíž konstruktor kopie je explicitní. Deklarování konstruktoru kopie jako `explicit` zabraňuje předávání/vracení objektů třídy do/z funkce. Další informace o explicitní konstruktory, naleznete v tématu [uživatelem definovaných převodů typu](../../cpp/user-defined-type-conversions-cpp.md).

1. Tento problém může dojít, když je proveden pokus o zkopírování instance třídy deklarované jako `const` pomocí kopírovací konstruktor, který nemá `const` odkazovat na parametr. Deklarujte konstruktor kopie s `const` zadejte místo odkazu na nekonstantní typ odkazu.