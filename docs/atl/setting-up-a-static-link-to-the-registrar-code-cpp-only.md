---
title: Nastavení statického odkazu na kód registrátoru (pouze C++)
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: b95bd17abca3237710956f3a1bf1b1d6fa9df51e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196662"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>Nastavení statického odkazu na kód registrátoru (pouze C++)

Klienti C++ můžete vytvářet statických odkazů na kód vašeho registrátora. Statické propojení vašeho registrátora analyzátor přidá přibližně 5K sestavení pro vydání.

Nejjednodušší způsob, jak nastavit statické propojení předpokládá, že jste zadali [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) v deklaraci objektu. (Toto je výchozí specifikaci používané knihovně ATL)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>Chcete-li vytvořit statické propojení pomocí DECLARE_REGISTRY_RESOURCEID

1. Zadejte [/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_statické\_REGISTRU** místo **/D \_ATL\_DLL**.

1. Znovu zkompilujte.

## <a name="see-also"></a>Viz také:

[Komponenta registru (Registrar)](../atl/atl-registry-component-registrar.md)
