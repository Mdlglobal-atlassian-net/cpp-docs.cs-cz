---
title: Přidání rozhraní ke zprostředkovateli
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: a1d219568c1787558674c47edd55436b8690a61c
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524811"
---
# <a name="adding-an-interface-to-your-provider"></a>Přidání rozhraní ke zprostředkovateli

> [!NOTE]
> Průvodce zprostředkovatele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším.

Určení objektu, který chcete přidat rozhraní do (obvykle datové zdroje, sady řádků, příkaz nebo relace objekty vytvořené **Průvodce zprostředkovatelem technologie OLE DB**). Je možné, že objekt je potřeba přidat rozhraní do je ten, který váš poskytovatel v současné době nepodporuje. V takovém případě spusťte **Průvodce zprostředkovatelem ATL OLE DB** k vytvoření objektu. Klikněte pravým tlačítkem na projekt v **zobrazení tříd**, klikněte na tlačítko **přidat** > **nová položka** v nabídce vyberte **nainstalováno**  >  **Visual C++** > **ATL**a potom klikněte na tlačítko **zprostředkovatele služeb OLEDB knihovny ATL**. Můžete chtít ukládejte kód rozhraní samostatný adresář a potom zkopírujte soubory do projektu poskytovatele.

Pokud jste vytvořili novou třídu pro podporu rozhraní, je objekt, který dědí z třídy. Můžete například přidat třídu `IRowsetIndexImpl` do objektu sady řádků:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Přidáte rozhraní do COM_MAP v objektu COM_INTERFACE_ENTRY – makro. Pokud neexistuje žádná mapa, vytvořte ji. Příklad:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

U objektu sady řádků řetězu mapu svého nadřazeného objektu objekt tak, aby objekt může delegovat na nadřazenou třídu. V tomto příkladu přidá dané makro COM_INTERFACE_ENTRY_CHAIN do mapy:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Viz také:

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)