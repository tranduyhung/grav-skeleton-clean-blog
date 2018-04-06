---
title: Contact Me
menu: Contact
subheading: Have questions? I have answers (maybe).
header_image: contact-bg.jpg

form:
    name: contact-form
    message_color: danger
    fields:
        -
            name: name
            label: THEME_CLEAN_BLOG.CONTACT.NAME
            placeholder: THEME_CLEAN_BLOG.CONTACT.NAME
            type: text
            validate:
                required: true
            classes: form-control
        -
            name: email
            label: THEME_CLEAN_BLOG.CONTACT.EMAIL
            placeholder: THEME_CLEAN_BLOG.CONTACT.EMAIL
            type: email
            validate:
                required: true
            classes: form-control
        -
            name: phone
            label: THEME_CLEAN_BLOG.CONTACT.PHONE
            placeholder: THEME_CLEAN_BLOG.CONTACT.PHONE
            type: text
            classes: form-control
        -
            name: message
            label: THEME_CLEAN_BLOG.CONTACT.MESSAGE
            placeholder: THEME_CLEAN_BLOG.CONTACT.MESSAGE
            type: textarea
            rows: 5
            validate:
                required: true
            classes: form-control
    buttons:
        -
            type: submit
            value: THEME_CLEAN_BLOG.CONTACT.SEND
            classes: btn btn-default
    process:
        - email:
            from: "{{ config.plugins.email.from }}"
            to:
                -
                    "{{ config.plugins.email.from }}"
            subject: "[Contact] {{ form.value.name|e }}"
            body: "{% include 'forms/data.html.twig' %}"
        - save:
            fileprefix: contact-
            dateformat: Ymd-His-u
            extension: txt
            body: "{% include 'forms/data.txt.twig' %}"
        - display: thank-you
        - reset: true
---

Want to get in touch with me? Fill out the form below to send me a message and I will try to get back to you within 24 hours!
