---
title: Předávání testů shodnosti technologie OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- conformance testing
- conformance testing [OLE DB]
- OLE DB providers, testing
ms.assetid: d1a4f147-2edd-476c-b452-0e6a0ac09891
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0288e1517bf89ec6ff8a2067311c3641d8d7113c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340913"
---
# <a name="passing-ole-db-conformance-tests"></a>Předávání testů shodnosti technologie OLE DB
Chcete-li poskytovatele konzistentnější, Data Access SDK poskytuje sadu testů shodnosti technologie OLE DB. Testy zkontrolujte všechny aspekty vašeho poskytovatele a poskytují rozumné záruku, že vaše zprostředkovatel funguje podle očekávání. Testů shodnosti technologie OLE DB můžete najít v sadě Microsoft Data Access SDK. Tato část se zaměřuje na věci, které byste měli udělat pro předávání testů shodnosti. Informace o spuštění testů shodnosti technologie OLE DB najdete v sadě SDK.  
  
## <a name="running-the-conformance-tests"></a>Spuštění testů shodnosti  
 Ve Visual C++ 6.0 přidali šablony zprostředkovatele OLE DB počet zapojených funkcí, které umožňují zkontrolovat hodnoty a vlastnosti. Většina těchto funkcí byly přidány v reakci na testů shodnosti.  
  
> [!NOTE]
>  Budete muset přidat několik ověřovací funkce pro předávání testů shodnosti technologie OLE DB poskytovatele.  
  
 Tento poskytovatel vyžaduje dvě rutiny ověřování. První rutina `CRowsetImpl::ValidateCommandID`, je součástí vaší třídy sady řádků. Je volána při vytváření sady řádků šablony zprostředkovatele. Ukázka používá tato rutina příjemci říct, že nepodporuje indexy. První volání `CRowsetImpl::ValidateCommandID` (Všimněte si, že poskytovatel použije `_RowsetBaseClass` typedef přidán v mapě rozhraní pro `CMyProviderRowset` v [Podpora zprostředkovatele pro záložky](../../data/oledb/provider-support-for-bookmarks.md), takže není potřeba psát tyto dlouhé řádky šablony argumenty). Pokud parametr indexu není NULL, pak se vraťte DB_E_NOINDEX (označuje, že uživatel chce používat indexu v USA). Další informace o ID příkazů najdete v příslušné specifikaci OLE DB a hledejte `IOpenRowset::OpenRowset`.  
  
 Následující kód je `ValidateCommandID` ověření rutinu:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
// Class: CMyProviderRowset   
  
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
  
 Šablony zprostředkovatele volají `OnPropertyChanged` metoda pokaždé, když někdo změní vlastnost na `DBPROPSET_ROWSET` skupiny. Pokud chcete zpracovávat vlastnosti pro jiné skupiny, je přidáte do příslušného objektu (to znamená, `DBPROPSET_SESSION` kontroly přejdou do `CMyProviderSession` třídy).  
  
 Kód nejprve zkontroluje, zda je vlastnost propojený na jiný. Když se tato vlastnost je zřetězená, nastaví `DBPROP_BOOKMARKS` vlastnost na hodnotu True. Příloha C specifikaci OLE DB obsahuje informace o vlastnostech. Tyto informace také zjistíte, zda je vlastnost zřetězené do jiného.  
  
 Můžete také přidat `IsValidValue` rutiny do vašeho kódu. Volání šablony `IsValidValue` při pokusu o nastavení vlastnosti. Tato metoda by se mělo přepsat, pokud vyžadují další zpracování při nastavení hodnoty vlastnosti. Můžete mít jednu z těchto metod pro každou sadu vlastností.  
  
## <a name="threading-issues"></a>Potíže s vlákny  
 Ve výchozím nastavení OLE DB Provider průvodce v průvodce zprostředkovatelem ATL OLE DB generuje kód pro zprostředkovatele pro spuštění v modelu objektu apartment. Při pokusu o spuštění tohoto kódu s testů shodnosti, získáte počáteční selhání. To je vzhledem k tomu bezplatné Ltm.exe, nástroj používaný ke spuštění testů shodnosti technologie OLE DB, výchozí hodnota je typu. Kód průvodce zprostředkovatelem technologie OLE DB výchozí model apartment pro výkon a jednoduché používání.  
  
 Chcete-li tento problém, můžete buď změnit LTM nebo změnit zprostředkovatele.  
  
#### <a name="to-change-ltm-to-run-in-apartment-threaded-mode"></a>Chcete-li změnit LTM ke spuštění v objektu apartment režimu vláken  
  
1.  V hlavní nabídce LTM **nástroje**a potom klikněte na tlačítko **možnosti**.  
  
2.  Na **Obecné** kartu, změňte model vláken ze **bezplatné vláken** k **s vlákny typu Apartment**.  
  
 Chcete-li změnit váš poskytovatel pro spuštění v režimu volného vláken:  
  
-   Hledání ve vašem projektu zprostředkovatele všechny výskyty `CComSingleThreadModel` a nahraďte ho hodnotou `CComMultiThreadModel`, který by měl být v hlavičkách zdroj, relace a sady řádků vaše data.  
  
-   V souboru .rgs změnit model vláken ze **objektu Apartment** k **obě**.  
  
-   Postupujte podle správné pravidel programování volných vláken programování (to znamená, že zámek zápisu).  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé techniky zprostředkování](../../data/oledb/advanced-provider-techniques.md)