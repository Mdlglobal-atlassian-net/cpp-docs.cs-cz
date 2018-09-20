---
title: Seznamy inicializátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 981f2737d370dc25ca4e7dc6c20947b3867a0c65
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394605"
---
# <a name="initializer-lists"></a>Inicializační seznamy

Seznamy inicializátorů konstruktorů jsou nyní volána před konstruktor základní třídy.

## <a name="remarks"></a>Poznámky

Před Visual C++ 2005 byla volána konstruktor základní třídy před seznamem inicializátorů při kompilaci spravovaného rozšíření jazyka C++. Nyní při kompilaci s **/CLR**, seznamem inicializátorů je jako první.

## <a name="see-also"></a>Viz také

[Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)