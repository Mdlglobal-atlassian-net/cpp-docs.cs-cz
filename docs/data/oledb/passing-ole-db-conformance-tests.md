---
title: Předávání testů shodnosti technologie OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
ms.openlocfilehash: eda4dccda147ddd4776bb56e649f539a7550abd1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209764"
---
# <a name="passing-ole-db-conformance-tests"></a>Předávání testů shodnosti technologie OLE DB

Pro zajištění větší konzistence zprostředkovatelů poskytuje sada Data Access SDK sadu OLE DBch testů shody. Testy kontrolují všechny aspekty poskytovatele a poskytují přiměřenou záruku, že poskytovatel funguje podle očekávání. V sadě Microsoft Data Access SDK můžete najít OLE DB testy shody. Tato část se zaměřuje na věci, které byste měli udělat, abyste vyhověli testům shody. Informace o spuštění testů shody OLE DB naleznete v sadě SDK.

## <a name="running-the-conformance-tests"></a>Spuštění testů shody

V jazyce C++ Visual 6,0 šablony poskytovatele OLE DB přidali množství funkcí vidlice, které umožňují kontrolu hodnot a vlastností. Většina těchto funkcí byla přidána v reakci na testy dodržování shody.

> [!NOTE]
> Je potřeba přidat několik funkcí ověřování pro poskytovatele, aby bylo možné předat OLE DB testy shody.

Tento zprostředkovatel vyžaduje dvě rutiny ověřování. První rutina, `CRowsetImpl::ValidateCommandID`, je součástí vaší třídy sady řádků. Je volána během vytváření sady řádků pomocí šablon zprostředkovatele. Ukázka používá tuto rutinu k oznámení příjemcům, že nepodporuje indexy. Prvním voláním je `CRowsetImpl::ValidateCommandID` (Všimněte si, že zprostředkovatel používá `_RowsetBaseClass` typedef přidaný v mapě rozhraní pro `CCustomRowset` v [podpoře poskytovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md), takže nemusíte zadávat dlouhý řádek argumentů šablony). Dále vraťte DB_E_NOINDEX, pokud parametr indexu není NULL (to znamená, že příjemce chce použít index na US). Další informace o ID příkazů naleznete v tématu OLE DB Specification a hledejte `IOpenRowset::OpenRowset`.

Následující kód je `ValidateCommandID` rutina ověřování:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H
// Class: CCustomRowset

HRESULT ValidateCommandID(DBID* pTableID, DBID* pIndexID)
{
   HRESULT hr = _RowsetBaseClass::ValidateCommandID(pTableID, pIndexID);
   if (hr != S_OK)
      return hr;

   if (pIndexID != NULL)
      return DB_E_NOINDEX;    // Doesn't support indexes

   return S_OK;
}
```

Šablony zprostředkovatele volají metodu `OnPropertyChanged` vždy, když někdo změní vlastnost ve skupině DBPROPSET_ROWSET. Chcete-li zpracovat vlastnosti pro jiné skupiny, přidejte je do příslušného objektu (to znamená, DBPROPSET_SESSION kontroly přecházejí do třídy `CCustomSession`).

Kód nejprve zkontroluje, zda je vlastnost propojena s jinou. Pokud je vlastnost zřetězena, nastaví vlastnost DBPROP_BOOKMARKS na hodnotu `True`. Příloha C specifikace OLE DB obsahuje informace o vlastnostech. Tyto informace také sdělují, zda je vlastnost zřetězena do jiné.

Můžete také chtít přidat rutinu `IsValidValue` do kódu. Šablony volají `IsValidValue` při pokusu o nastavení vlastnosti. Tuto metodu byste měli přepsat, pokud při nastavování hodnoty vlastnosti požadujete další zpracování. Jednu z těchto metod můžete pro každou sadu vlastností nastavit.

## <a name="see-also"></a>Viz také

[Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)
