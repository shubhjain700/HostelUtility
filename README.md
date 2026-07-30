# Hostel Utility

An Android app that gives hostel residents a single place to raise complaints, file
applications and read notices — and gives hostel officials a dashboard to act on them.

> **Archived university project (Feb – Apr 2020).** Built during my B.Tech at GLA
> University while I was learning Android. It is kept public as a record of early work —
> it targets Android 9 (API 28) and is no longer maintained. For current work see
> [my portfolio](https://shubham-portfolio-opal.vercel.app).

## What it does

**For students**
- Register against a college and hostel, with room number and guardian contact details
- Raise complaints at the individual or whole-hostel level
- File applications — leave, net refill requests and similar
- Browse a staff and faculty directory
- Set a profile photo, cropped and compressed on-device before upload

**For hostel officials**
- A card-grid dashboard as the single entry point to every module
- Review incoming student complaints and applications
- Publish notices, either typed or picked from the gallery

## Built with

| | |
| :--- | :--- |
| Language | Java |
| Min / target SDK | 19 / 28 |
| UI | AndroidX, Material Components, ConstraintLayout + MotionLayout, RecyclerView, CardView |
| Images | Glide, Android Image Cropper, Compressor |
| Other | Gson, Firebase Analytics, Crashlytics |

The screens follow a hand-rolled **MVP** pattern — `BaseActivity<V, P>` wires each view to
its presenter, with `IODashboardView` / `IODashboardPresenter` and `DashBoardBean` as the
contract for the dashboard. It was my first attempt at separating presentation from view
logic rather than putting everything in the `Activity`.

## Running it

```bash
git clone https://github.com/shubhjain700/HostelUtility.git
cd HostelUtility
./gradlew assembleDebug
```

Or open the folder in Android Studio and run the `app` configuration.

The build expects an `app/google-services.json`. The committed one points at a Firebase
project that is no longer active — replace it with your own from the
[Firebase console](https://console.firebase.google.com) before building.

## Honest caveats

This is student work from 2020, warts and all:

- Analytics and Crashlytics are wired up, but there is **no networked backend** in this
  snapshot — the data layer is local, so the app is effectively a working UI prototype.
- The registration form collects sensitive fields (Aadhaar, guardian phone) with no
  encryption or consent flow. Do not point this at real data.
- Naming is inconsistent (`choose_college` alongside `StudentComplaintsActivity`), and
  the dependency versions are long out of date.
