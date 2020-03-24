---
title: Přidání rozhraní ke zprostředkovateli
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB provider templates, object interfaces
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
ms.openlocfilehash: b13d1224388dc7d3218dea1c70b5aa8a595fcbdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212328"
---
# <a name="adding-an-interface-to-your-provider"></a>Přidání rozhraní ke zprostředkovateli

> [!NOTE]
> Průvodce zprostředkovatelem OLE DB ATL není k dispozici v aplikaci Visual Studio 2019 a novější.

Určete, do kterého objektu chcete přidat rozhraní (obvykle zdroj dat, sada řádků, příkazy nebo objekty relace vytvořené **průvodcem poskytovatelem OLE DB**). Je možné, že objekt, ke kterému potřebujete přidat rozhraní, je ten, který váš poskytovatel aktuálně nepodporuje. V takovém případě spusťte **Průvodce ATL OLE DB Provider** pro vytvoření objektu. V **zobrazení tříd**klikněte pravým tlačítkem myši na projekt, v nabídce klikněte na možnost **Přidat** > **novou položku** , vyberte možnost **nainstalované** > **Visual C++**  > **ATL**a pak klikněte na možnost **ATL OLE Provider**. Kód rozhraní můžete chtít vložit do samostatného adresáře a potom zkopírovat soubory do projektu poskytovatele.

Pokud jste vytvořili novou třídu pro podporu rozhraní, zajistěte, aby objekt dědil z této třídy. Například je možné přidat třídu `IRowsetIndexImpl` do objektu sady řádků:

```cpp
template <class Creator>
class CCustomRowset :
    public CRowsetImpl< CCustomRowset<Creator>, CCustomWindowsFile, Creator>,
    public IRowsetIndexImpl< ... >
```

Přidejte rozhraní, které se COM_MAP v objektu pomocí makra COM_INTERFACE_ENTRY. Pokud žádná mapa neexistuje, vytvořte ji. Příklad:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
END_COM_MAP()
```

Pro objekt sady řádků zřetězení mapy jeho nadřazeného objektu, aby objekt mohl delegovat na nadřazenou třídu. V tomto příkladu přidejte COM_INTERFACE_ENTRY_CHAIN makro do mapy:

```cpp
BEGIN_COM_MAP(CCustomRowset)
     COM_INTERFACE_ENTRY(IRowsetIndex)
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)
END_COM_MAP()
```

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
