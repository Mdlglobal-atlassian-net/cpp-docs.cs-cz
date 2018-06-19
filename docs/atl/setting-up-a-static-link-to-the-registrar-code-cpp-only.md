---
title: Nastavení statické odkaz na kód registrátora (C++ pouze) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dca93c8f0fcae578700a9d9970977179fbd142d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360185"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Nastavení statické odkaz na kód registrátora (pouze C++)
C++ klientů může vytvořit statický odkaz kódu vašeho registrátora. Statické propojení vašeho registrátora analyzátor přidá přibližně 5K sestavení pro vydání.  
  
 Nejjednodušší způsob, jak nastavit statické propojení předpokládá, že jste zadali [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) v deklaraci tohoto objektu. (Toto je výchozí specifikaci používané ATL.)  
  
### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Chcete-li vytvořit statický odkaz pomocí DECLARE_REGISTRY_RESOURCEID  
  
1.  Zadejte [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` místo /D **_ATL_DLL**.  
  
2.  Pak ji znovu zkompilovat.  
  
## <a name="see-also"></a>Viz také  
 [Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)

