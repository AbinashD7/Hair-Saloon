# Hair-Saloon

## Email confirmations

Appointment confirmation emails use SMTP when `EMAIL_HOST_USER` and
`EMAIL_HOST_PASSWORD` are set. Without these credentials, Django prints the
email to the development server console.

For Gmail, enable 2-Step Verification and create an App Password for this app.
In the same PowerShell window used to start Django, set:

```powershell
$env:EMAIL_HOST_USER = "your-address@gmail.com"
$env:EMAIL_HOST_PASSWORD = "your-16-character-app-password"
$env:DEFAULT_FROM_EMAIL = $env:EMAIL_HOST_USER
```

Then start the server from that PowerShell window. Do not use your regular
Gmail password or commit SMTP credentials to the repository. The defaults are
Gmail SMTP (`smtp.gmail.com:587` with TLS); other SMTP providers can be
configured with `EMAIL_HOST`, `EMAIL_PORT`, and `EMAIL_USE_TLS` environment
variables. For providers that require implicit SSL, set `EMAIL_USE_TLS` to
`False` and `EMAIL_USE_SSL` to `True`. TLS and SSL cannot both be enabled.
Both `EMAIL_HOST_USER` and `EMAIL_HOST_PASSWORD` are required to activate
SMTP; a partially configured credential pair is reported as a configuration
error instead of silently falling back to the console.