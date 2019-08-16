---
title: CSemaphore – třída
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: d5a0e4187107aaab7cedf4e7a0e2fc47b9f9f305
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502586"
---
# <a name="csemaphore-class"></a>CSemaphore – třída

Objekt třídy `CSemaphore` představuje "semafor" – synchronizační objekt, který umožňuje omezenému počtu vláken v jednom nebo více procesech pro přístup k zachovává počet vláken, která aktuálně přistupují k určitému prostředku.

## <a name="syntax"></a>Syntaxe

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|`CSemaphore` Vytvoří objekt.|

## <a name="remarks"></a>Poznámky

Semafory jsou užitečné při řízení přístupu ke sdílenému prostředku, který může podporovat jenom omezený počet uživatelů. Aktuální počet `CSemaphore` objektů je povolený počet dalších uživatelů. Pokud počet dosáhne nuly, všechny pokusy o použití zdroje kontrolovaného `CSemaphore` objektem budou vloženy do systémové fronty a budou čekat na vypršení časového limitu nebo nárůst počtu na hodnotu 0. Maximální počet uživatelů, kteří mají v jednom okamžiku přístup k řízenému prostředku, je určen během konstrukce `CSemaphore` objektu.

Chcete-li `CSemaphore` použít objekt, `CSemaphore` Sestavte objekt, když je potřeba. Zadejte název semaforu, na kterém chcete čekat, a aplikaci, kterou by měla aplikace zpočátku vlastnit. Pak můžete přístup k semaforu, když se konstruktor vrátí. Zavolejte [CSyncObject:: Unlock](../../mfc/reference/csyncobject-class.md#unlock) , když jste dokončili přístup k řízenému prostředku.

Alternativním způsobem použití `CSemaphore` objektů je přidat proměnnou typu `CSemaphore` jako datový člen do třídy, kterou chcete ovládat. Během konstrukce kontrolovaného objektu zavolejte konstruktor `CSemaphore` datového členu, který určuje počáteční počet přístupů, maximální počet přístupů, název semaforu (Pokud se bude používat napříč hranicemi procesu) a požadované atributy zabezpečení.

Chcete-li získat přístup `CSemaphore` k prostředkům řízenými objekty tímto způsobem, nejprve vytvořte proměnnou typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo do funkce člena přístupu prostředku zadejte [CMultiLock](../../mfc/reference/cmultilock-class.md) . Pak zavolejte `Lock` členskou funkci objektu zámku (například [CSingleLock:: Lock](../../mfc/reference/csinglelock-class.md#lock)). V tomto okamžiku vaše vlákno získá přístup k prostředku, počká na uvolnění prostředku a získá přístup, nebo počkejte na uvolnění prostředku a vypršení časového limitu, čímž se nepodaří získat přístup k prostředku. V každém případě byl k vašemu prostředku přístup bezpečným způsobem. Chcete-li uvolnit prostředek, použijte `Unlock` členskou funkci objektu zámku (například [CSingleLock:: Unlock](../../mfc/reference/csinglelock-class.md#unlock)), nebo umožněte objektu zámku, aby se z oboru nevrátil.

Alternativně můžete vytvořit `CSemaphore` objekt samostatně a přistupovat k němu explicitně před tím, než se pokusíte o přístup k kontrolovanému prostředku. Tato metoda, zatímco od někoho srozumitelného čte váš zdrojový kód, je náchylná k chybě.

Další informace o použití `CSemaphore` objektů naleznete v článku [Multithreading: Jak používat synchronizační třídy](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt. h

##  <a name="csemaphore"></a>CSemaphore::CSemaphore

Vytvoří pojmenovaný nebo nepojmenovaný `CSemaphore` objekt.

```
CSemaphore(
    LONG lInitialCount = 1,
    LONG lMaxCount = 1,
    LPCTSTR pstrName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttributes = NULL);
```

### <a name="parameters"></a>Parametry

*lInitialCount*<br/>
Počáteční počet použití pro semafor. Musí být větší než nebo rovno 0 a menší nebo rovno *lMaxCount*.

*lMaxCount*<br/>
Maximální počet použití pro semafor. Musí být větší než 0.

*pstrName*<br/>
Název semaforu Je nutné zadat, pokud bude semafor k dispozici napříč hranicemi procesu. Pokud `NULL`dojde k pojmenování objektu. Pokud se název shoduje s existujícím semaforem, konstruktor vytvoří nový `CSemaphore` objekt, který odkazuje na semafor daného názvu. Pokud se název shoduje se stávajícím synchronizačním objektem, který není semafor, konstrukce se nezdaří.

*lpsaAttributes*<br/>
Atributy zabezpečení pro objekt semaforu Úplný popis této struktury naleznete v tématu [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) v Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li získat přístup `CSemaphore` k objektu nebo ho uvolnit, vytvořte objekt [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho funkci [Lock](../../mfc/reference/csinglelock-class.md#lock) a [Odemkněte](../../mfc/reference/csinglelock-class.md#unlock) členské funkce.

> [!IMPORTANT]
>  Po vytvoření `CSemaphore` objektu použijte příkaz [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby se zajistilo, že mutex ještě neexistuje. Pokud Mutex neočekávaně existoval, může to znamenat, že neoprávněný proces je squatting a může vycházet z škodlivého použití mutexu. V tomto případě je doporučený postup pro zaznamenání zabezpečení zavřít a pokračovat, jako kdyby došlo k chybě při vytváření objektu.

## <a name="see-also"></a>Viz také:

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
