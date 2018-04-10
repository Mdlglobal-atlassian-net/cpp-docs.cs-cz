---
title: Inicializační seznamy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1af020bec295f0f949b7ebb6abe88102f3942b1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="initializer-lists"></a>Inicializační seznamy
Inicializační seznamy v konstruktorech se nyní nazývají před konstruktor základní třídy.  
  
## <a name="remarks"></a>Poznámky  
 Před Visual C++ 2005 byla volána konstruktor základní třídy před inicializačním seznam při kompilaci s spravovaných rozšíření jazyka C++. Teď když kompilujete s **/CLR**, inicializátoru seznamu jako první.  
  
## <a name="see-also"></a>Viz také  
 [Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)