---
title: Inicializační seznamy | Microsoft Docs
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
ms.openlocfilehash: 6634b749480e5108548de0c8b53f8b09cc5a42c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127949"
---
# <a name="initializer-lists"></a>Inicializační seznamy
Inicializační seznamy v konstruktorech se nyní nazývají před konstruktor základní třídy.  
  
## <a name="remarks"></a>Poznámky  
 Před Visual C++ 2005 byla volána konstruktor základní třídy před inicializačním seznam při kompilaci s spravovaných rozšíření jazyka C++. Teď když kompilujete s **/CLR**, inicializátoru seznamu jako první.  
  
## <a name="see-also"></a>Viz také  
 [Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)