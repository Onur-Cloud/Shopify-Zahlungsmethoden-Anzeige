# Shopify Zahlungsmethoden-Anzeige mit Übersetzung

Dieses Snippet fügt eine kompakte, optimierte und übersetzbare Anzeige der verfügbaren Zahlungsmethoden zu Ihrem Shopify-Theme hinzu.

## Vorschau

### Desktop-Ansicht
![Desktop-Ansicht](https://i.ibb.co/ggKqM5V/image.png)

### Mobile-Ansicht
![Mobile-Ansicht](https://i.ibb.co/d668kdm/image.png)

## Installation

1. Gehen Sie in Ihrem Shopify-Admin zu "Online Store" > "Themes".
2. Klicken Sie auf "Customize" bei Ihrem aktuellen Theme.
3. Wählen Sie im Theme Editor den Bereich aus, wo Sie die Zahlungsmethoden anzeigen möchten (z.B. Footer).
4. Klicken Sie auf "Add section" und wählen Sie "Custom liquid".
5. Kopieren Sie den folgenden Code und fügen Sie ihn in den Custom liquid-Bereich ein:

```liquid
{% style %}
.ss-pay {
  background: #f8f8f8;
  border: 1px solid #e0e0e0;
  border-radius: 6px;
  padding: 10px;
  margin-top: 10px;
  text-align: center;
}
.ss-pay h2 {
  font-size: 14px;
  margin: 0 0 8px;
}
.ss-pay ul {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 8px;
  padding: 0;
  margin: 0;
  list-style: none;
}
.ss-pay svg {
  width: 35px;
  height: auto;
}
.ss-pay p {
  font-size: 11px;
  color: #666;
  margin: 8px 0 0;
}
{% endstyle %}

<div class="ss-pay">
  <h2>{{ 'general.payment.methods_title' | t }}</h2>
  <ul>
    {% for type in shop.enabled_payment_types %}
      <li>{{ type | payment_type_svg_tag }}</li>
    {% endfor %}
    {% unless shop.enabled_payment_types contains 'klarna' %}
      <li><!-- Klarna SVG --></li>
    {% endunless %}
  </ul>
  <p>{{ 'general.payment.secure_transactions' | t }}</p>
</div>
```

6. Klicken Sie auf "Save".

## Übersetzungen hinzufügen

Um Übersetzungen für verschiedene Sprachen hinzuzufügen:

1. Gehen Sie in Ihrem Shopify-Admin zu "Online Store" > "Themes".
2. Klicken Sie bei Ihrem aktiven Theme auf "Actions" > "Edit languages".
3. Scrollen Sie zum Abschnitt "General" und fügen Sie folgende Übersetzungen hinzu:

   ```
   general:
     payment:
       methods_title: Sichere Zahlungsmethoden
       secure_transactions: SSL-verschlüsselte Transaktionen
   ```

4. Fügen Sie Übersetzungen für alle Sprachen hinzu, die Ihr Shop unterstützt.

## Anpassung

Sie können den Stil direkt im Custom liquid-Code anpassen:

- Ändern Sie die Farben durch Anpassen der `background`, `border`, und `color` Werte.
- Verändern Sie die Größen durch Anpassen der `font-size` und `width` Werte.

## Unterstützung

Bei Fragen oder Problemen wenden Sie sich bitte an den Shopify-Support oder konsultieren Sie die Shopify-Community-Foren.
