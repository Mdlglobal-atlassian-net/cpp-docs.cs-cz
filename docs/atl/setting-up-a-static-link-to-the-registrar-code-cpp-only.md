---
title: Nastavení statického odkazu na kód registrátoru (pouze C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 7a66ca33aa95ea6ffd59860cf0a55e51266ef5cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757695"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Nastavení statického odkazu na kód registrátoru (pouze C++)

Klienti C++ můžete vytvářet statických odkazů na kód vašeho registrátora. Statické propojení vašeho registrátora analyzátor přidá přibližně 5K sestavení pro vydání.

Nejjednodušší způsob, jak nastavit statické propojení předpokládá, že jste zadali [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) v deklaraci objektu. (Toto je výchozí specifikaci používané knihovně ATL)

### <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Chcete-li vytvořit statické propojení pomocí DECLARE_REGISTRY_RESOURCEID

1. Zadejte [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` místo /D **_ATL_DLL**.

2. Znovu zkompilujte.

## <a name="see-also"></a>Viz také

[Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)

