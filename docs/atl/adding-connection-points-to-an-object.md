---
title: Přidání bodů připojení objektu
ms.date: 11/04/2016
helpviewer_keywords:
- connection points [C++], adding to ATL objects
- Implement Connection Point ATL wizard
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
ms.openlocfilehash: bf3819f96821b8794b6bd120d63798b902eb2b9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473798"
---
# <a name="adding-connection-points-to-an-object"></a>Přidání bodů připojení objektu

[ATL – tutoriál](../atl/active-template-library-atl-tutorial.md) ukazuje, jak vytvořit ovládací prvek s podporou pro spojovací body, přidejte události a implementovat bod připojení. Implementuje ATL – body připojení [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) třídy.

Implementace bodu připojení, máte dvě možnosti:

- Implementujte vlastní odchozí zdroj události, tak, že přidáte ovládací prvek nebo objektu spojovacího bodu.

- Znovu použít bod připojení rozhraní definované v jiné knihovny typů.

Průvodce implementací bodu připojení v obou případech se používá knihovnu typů ke své práci.

### <a name="to-add-a-connection-point-to-a-control-or-object"></a>Chcete-li přidat bod připojení na ovládací prvek nebo objekt

1. Definování dispinterface v bloku knihovny ze souboru IDL. Pokud je povolena podpora pro spojovací body při tvorbě ovládacího prvku pomocí Průvodce ovládacími prvky ATL, dispinterface už vytvořili. Pokud jste nepovolili podporu pro spojovací body při tvorbě ovládacího prvku, je třeba ručně přidat dispinterface do souboru IDL. Následuje příklad dispinterface. Odchozí rozhraní nejsou musí být odesílajících rozhraních, ale mnoho skriptovacích jazyků, jako jsou VBScript a JScript vyžadují, proto tento příklad používá dva odesílající rozhraní:

   [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/cpp/adding-connection-points-to-an-object_1.idl)]

   Pomocí nástroje uuidgen.exe nebo guidgen.exe generování identifikátoru GUID.

2. Přidat dispinterface jako `[default,source]` rozhraní v konstruktoru coclass pro objekt v souboru IDL projektu. Znovu, pokud je povolena podpora pro spojovací body při tvorbě ovládacího prvku, Průvodce ovládacím prvkem ATL vytvoří `[default,source`] položka. Chcete-li ručně přidat tuto položku, přidejte řádek tučně:

   [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/cpp/adding-connection-points-to-an-object_2.idl)]

   Soubor .idl [KR](../visual-cpp-samples.md) ukázky knihovny ATL pro příklad.

3. Zobrazení tříd můžete přidat vlastnosti a metody pro rozhraní události. Klikněte pravým tlačítkem na třídu v zobrazení tříd, přejděte na **přidat** na místní nabídku a klikněte na **přidat bod připojení**.

4. V **rozhraní zdroje** seznam nebo Průvodce implementací bodu připojení, vyberte pole **rozhraních projektu**. Pokud se rozhodnete rozhraní pro řízení a stisknutím klávesy **OK**, bude:

   - Generovat soubor hlaviček s proxy třída události, která implementuje kód, který bude provádět odchozích volání pro událost.

   - Přidáte položku do mapy bodu připojení.

   Zobrazí se také seznam všech knihoven typů ve vašem počítači. Byste měli používat jenom jednu z těchto jiných knihovnách typů k definování spojovací bod, pokud chcete implementovat přesně stejné odchozí rozhraní v jiné knihovny typů.

### <a name="to-reuse-a-connection-point-interface-defined-in-another-type-library"></a>Pro opětovné použití rozhraní bodu připojení definovaný v jiné knihovny typů

1. V zobrazení tříd klikněte pravým tlačítkem na třídu, která implementuje **BEGIN_COM_MAP** – makro, přejděte na příkaz **přidat** na místní nabídku a klikněte na **přidat bod připojení**.

2. V průvodce implementací bodu připojení, vyberte knihovnu typů a rozhraní v knihovně typů a klikněte na tlačítko **přidat**.

3. Upravte soubor .idl buď:

   - Zkopírujte dispinterface v souboru IDL pro objekt, jehož zdroje událostí se používá.

   - Použití **importlib** instrukce na tuto knihovnu typů.

## <a name="see-also"></a>Viz také

[Spojovací bod](../atl/atl-connection-points.md)

