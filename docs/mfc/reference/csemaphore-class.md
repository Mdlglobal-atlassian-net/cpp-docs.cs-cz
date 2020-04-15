---
title: Třída CSemaphore
ms.date: 11/04/2016
f1_keywords:
- CSemaphore
- AFXMT/CSemaphore
- AFXMT/CSemaphore::CSemaphore
helpviewer_keywords:
- CSemaphore [MFC], CSemaphore
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
ms.openlocfilehash: 26e1fd55d321b221f4732874d57d02a79c4c6398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318504"
---
# <a name="csemaphore-class"></a>Třída CSemaphore

Objekt třídy `CSemaphore` představuje "semafor" – objekt synchronizace, který umožňuje omezený počet podprocesů v jednom nebo více procesech pro přístup udržuje počet podprocesů aktuálně přístup k zadanému prostředku.

## <a name="syntax"></a>Syntaxe

```
class CSemaphore : public CSyncObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSemaphore::CSemaphore](#csemaphore)|Vytvoří `CSemaphore` objekt.|

## <a name="remarks"></a>Poznámky

Semafory jsou užitečné při řízení přístupu ke sdílenému prostředku, který může podporovat pouze omezený počet uživatelů. Aktuální počet `CSemaphore` objektů je počet dalších uživatelů povoleno. Když počet dosáhne nuly, všechny pokusy o `CSemaphore` použití prostředku řízeného objektem budou vloženy do systémové fronty a počkejte, dokud nedosáhnou časového režimu nebo se počet zvýší nad 0. Maximální počet uživatelů, kteří mají přístup k řízenému prostředku `CSemaphore` najednou, je určen během výstavby objektu.

Chcete-li `CSemaphore` použít objekt, vytvořte objekt, `CSemaphore` když je potřeba. Zadejte název semaforu, na který chcete čekat, a že aplikace by ji měla zpočátku vlastnit. Potom můžete přistupovat k semaforu, když se vrátí konstruktor. Volání [CSyncObject::Unlock](../../mfc/reference/csyncobject-class.md#unlock) po dokončení přístupu k řízenému prostředku.

Alternativní metodou pro `CSemaphore` použití objektů je přidání `CSemaphore` proměnné typu jako datového člena do třídy, kterou chcete řídit. Během vytváření řízeného objektu zavolejte `CSemaphore` konstruktor datového člena určující počáteční počet přístupu, maximální počet přístupu, název semaforu (pokud bude použit přes hranice procesu) a požadované atributy zabezpečení.

Chcete-li získat `CSemaphore` přístup k prostředkům řízenýobjektů tímto způsobem, nejprve vytvořte proměnnou buď typu [CSingleLock](../../mfc/reference/csinglelock-class.md) nebo [cmultilock](../../mfc/reference/cmultilock-class.md) v přístupové členské funkce prostředku. Potom volání `Lock` členské funkce objektu lock (například [CSingleLock::Lock).](../../mfc/reference/csinglelock-class.md#lock) V tomto okamžiku vlákno buď získat přístup k prostředku, počkejte na prostředek, který má být uvolněn a získat přístup, nebo čekat na prostředek, který má být uvolněn a časový režim, nedaří získat přístup k prostředku. V každém případě byl přístup k prostředku přístupným způsobem bezpečným pro přístup z více vláken. Chcete-li uvolnit prostředek, použijte `Unlock` člennou funkci objektu zámku (například [CSingleLock::Unlock)](../../mfc/reference/csinglelock-class.md#unlock)nebo povolte, aby objekt zámku vypadl z oboru.

Případně můžete vytvořit `CSemaphore` samostatný objekt a získat k němu explicitně přístup před pokusem o přístup k řízenému prostředku. Tato metoda, zatímco jasnější pro někoho čtení zdrojového kódu, je náchylnější k chybě.

Další informace o použití `CSemaphore` objektů naleznete v článku [Vícevláken: Jak používat třídy synchronizace](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Objekt CSyncObject](../../mfc/reference/csyncobject-class.md)

`CSemaphore`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxmt.h

## <a name="csemaphorecsemaphore"></a><a name="csemaphore"></a>CSemaphore::CSemaphore

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
Počáteční počet využití pro semafor. Musí být větší nebo rovno 0 a menší než nebo rovno *lMaxCount*.

*lPočet maxů*<br/>
Maximální počet využití pro semafor. Musí být větší než 0.

*název pstr*<br/>
Název semaforu. Musí být zadán, pokud semafor bude přistupovat přes hranice procesu. Pokud `NULL`bude objekt nepojmenovaný. Pokud název odpovídá existující semafor, konstruktor vytvoří `CSemaphore` nový objekt, který odkazuje na semafor tohoto názvu. Pokud název odpovídá existující objekt synchronizace, který není semafor, konstrukce se nezdaří.

*atributy lpsa*<br/>
Atributy zabezpečení objektu semaforu. Úplný popis této struktury naleznete v [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) sady Windows SDK.

### <a name="remarks"></a>Poznámky

Chcete-li získat `CSemaphore` přístup nebo uvolnit objekt, vytvořte objekt [CMultiLock](../../mfc/reference/cmultilock-class.md) nebo [CSingleLock](../../mfc/reference/csinglelock-class.md) a zavolejte jeho členské funkce [Lock](../../mfc/reference/csinglelock-class.md#lock) and [Unlock.](../../mfc/reference/csinglelock-class.md#unlock)

> [!IMPORTANT]
> Po vytvoření `CSemaphore` objektu použijte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) k zajištění, že mutex ještě neexistoval. Pokud mutex existoval neočekávaně, může to znamenat, že proces rogue je squatting a může být v úmyslu použít mutex zlomyslně. V tomto případě je doporučená procedura s ohledem na zabezpečení zavřít popisovač a pokračovat, jako by došlo k chybě při vytváření objektu.

## <a name="see-also"></a>Viz také

[CSyncObject – třída](../../mfc/reference/csyncobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
