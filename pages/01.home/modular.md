---
title: Appi
menu: Home
classes:
cache_enable: false
content:
    items: '@self.modular'
    order:
        by: default
        dir: asc
        custom:
            - _herohome
            - _highlights
            - _details
            - _subscription
            - _footernavigation

form:
    action: /home
    name: subscription-form
    classes: contact
    fields:
        -
            name: code
            type: select
            default: 1
            options:
                1: US (+1)
                36: Hungary (+36)
                84: Vietnam (+84)
        -
            name: number
            type: text
            required: true
            classes: text phoneNumber
            placeholder: Phone number

    buttons:
        -
            type: submit
            value: Submit
            classes: submit appended

    process:
        -
            email:
                from: "{{ config.plugins.email.from }}"
                to:
                    - "{{ config.plugins.email.from }}"
            subject: "[Subscription] {{ form.value.code|e ~ form.value.number|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        -
            save:
                fileprefix: subscription-
                dateformat: Ymd-His-u
                extension: txt
                body: "{% include 'forms/data.txt.twig' %}"
        -
            display: thank-you
---
