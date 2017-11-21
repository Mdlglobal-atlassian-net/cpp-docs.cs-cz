---
title: "Nastavení statické odkaz na kód registrátora (C++ pouze) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b8eb77bc6f99ab6b7d8ca9d51f1a7a8549d8f0c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Nastavení statické odkaz na kód registrátora (pouze C++)
C++ klientů může vytvořit statický odkaz kódu vašeho registrátora. Statické propojení vašeho registrátora analyzátor přidá přibližně 5K sestavení pro vydání.  
  
 Nejjednodušší způsob, jak nastavit statické propojení předpokládá, že jste zadali [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) v deklaraci tohoto objektu. (Toto je výchozí specifikaci používané ATL.)  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Chcete-li vytvořit statický odkaz pomocí DECLARE_REGISTRY_RESOURCEID  
  
1.  Zadejte [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` místo /D**_ATL_DLL**.  
  
2.  Pak ji znovu zkompilovat.  
  
## <a name="see-also"></a>Viz také  
 [Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)

