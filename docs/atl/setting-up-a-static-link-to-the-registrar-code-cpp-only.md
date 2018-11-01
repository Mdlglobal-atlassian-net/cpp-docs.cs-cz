---
title: Nastavení statického odkazu na kód registrátoru (pouze C++)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: e5f09ce4626e030c43ecc30ca44d1ac738341c6c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557406"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Nastavení statického odkazu na kód registrátoru (pouze C++)

Klienti C++ můžete vytvářet statických odkazů na kód vašeho registrátora. Statické propojení vašeho registrátora analyzátor přidá přibližně 5K sestavení pro vydání.

Nejjednodušší způsob, jak nastavit statické propojení předpokládá, že jste zadali [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) v deklaraci objektu. (Toto je výchozí specifikaci používané knihovně ATL)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Chcete-li vytvořit statické propojení pomocí DECLARE_REGISTRY_RESOURCEID

1. Zadejte [/D](../build/reference/d-preprocessor-definitions.md) `_ATL_STATIC_REGISTRY` místo /D **_ATL_DLL**.

1. Znovu zkompilujte.

## <a name="see-also"></a>Viz také

[Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)
