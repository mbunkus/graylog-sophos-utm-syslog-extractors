# Graylog extractors for Sophos UTM 9 standard syslog fields

The Sophos UTM remote syslog capabilities use a non-standard message
format. Importing them into Graylog requires the use of a "Raw/plain
text" input (either TCP or UDP will be fine) together with a
extractors parsing the lines into the standard syslog fields.

The extractors in this repository will do the following:

1. Extract the fields `facility`, `level`, `source`,
   `application_name` and `process_id` (only if present in the line;
   e.g. it won't be with kernel messages) and
2. modify the `message` field not to contain the fields extracted in
   step 1.

As the change in step 2 is destructive, the extractor named `Syslog
field "message"` **must** be the last extractor in the list.

## Installation

1. In Graylog, create an input of type `Raw/Plaintext (TCP)` or
   `Raw/Plaintext (UDP)`.
2. After creating the input, click on the corresponding `Manage
   extractors` button.
3. In the upper right click on `Actions` and select `Import
   extractors`.
4. Copy & paste the extractors from the
   [`extractors.json`](extractors.json) file in this repository.
5. Optionally use the `Sort extractors` button after importing
   them. Like stated above, make sure the `Syslog field "message"`
   extractor is the last one run.

## Other extractors

User [habibmbacfou](https://github.com/habibmbacfou/graylogzeus)
provides extractors for various other fields in the `message`
parts. Their extractors can be used with my extractors at the same
time.

## Contact

I appreciate bug reports or merge requests. You can also contact me at
m.bunkus@linet-services.de
