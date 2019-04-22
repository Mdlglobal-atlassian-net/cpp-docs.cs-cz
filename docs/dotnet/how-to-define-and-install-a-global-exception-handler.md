---
title: 'Postupy: Definování a instalace globální obslužné rutiny výjimek'
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: d1b8452d19172bf16817c36032189accfd855539
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58777204"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>Postupy: Definování a instalace globální obslužné rutiny výjimek

Následující příklad kódu ukazuje, jak neošetřené výjimky mohou být zachyceny. Ukázkový formulář obsahuje tlačítka, který při stisknutí, provádí odkaz s hodnotou null, což způsobí vyvolání výjimky. Tato funkce představuje typické kód selhání. Výsledný výjimka zachycena ve funkci main nainstalované obslužná rutina výjimky celou aplikaci.

To lze provést pomocí vazby delegáta, kterého <xref:System.Windows.Forms.Application.ThreadException> událostí. V tomto případě následující výjimky jsou potom odeslány `App::OnUnhandled` metody.

## <a name="example"></a>Příklad

```
// global_exception_handler.cpp
// compile with: /clr
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Drawing;
using namespace System::Windows::Forms;

ref class MyForm : public Form
{
   Button^ b;
public:
   MyForm( )
   {
      b = gcnew Button( );
      b->Text = "Do Null Access";
      b->Size = Drawing::Size(150, 30);
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);
      Controls->Add(b);
   }
   void OnClick(Object^ sender, EventArgs^ args)
   {
      // do something illegal, like call through a null pointer...
      Object^ o = nullptr;
      o->ToString( );
   }
};

ref class App
{
public:
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)
   {
      MessageBox::Show(e->Exception->Message, "Global Exeception");
      Application::ExitThread( );
   }
};

int main()
{
   Application::ThreadException += gcnew
      ThreadExceptionEventHandler(App::OnUnhandled);

   MyForm^ form = gcnew MyForm( );
   Application::Run(form);
}
```

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../extensions/exception-handling-cpp-component-extensions.md)
