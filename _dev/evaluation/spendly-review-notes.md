# Spendly Evaluation Notes

This is a development/evaluation fixture, not shipped as plugin runtime content.

Observed weaknesses in the first generated API_DESIGN.md:

1. Endpoint design appeared before major user decisions were confirmed.
2. JWT was selected largely because "statelessness" was desired; authentication mechanism should be evaluated against actual clients and browser security.
3. `localStorage` was suggested as a JWT storage location without sufficiently discussing XSS/token exposure.
4. `PUT` was used for a request containing optional fields; this is more naturally a PATCH candidate unless full replacement semantics are intended.
5. Versioning used `/v1` plus semantic minor/patch version claims. URL major-versioning does not mean the URL should encode minor/patch versions.
6. Public caching was suggested for authenticated profile/analytics data before establishing cache visibility.
7. Monetary values were represented as floats.
8. Logout semantics were ambiguous because stateless JWT logout does not inherently invalidate a token.
9. Analytics was treated as "functional endpoints" without first deciding whether these are read models/queries/subresources.
10. The design included many implementation-level details despite being design-only.
11. `health` endpoint was proposed without establishing an operational consumer.
12. Rate limiting/storage recommendations introduced Redis without a requirement for it.
13. Status code policy was broad but did not establish when 400 vs 422 should be used.
14. The design lacked an explicit decision gate between domain/resource modeling and endpoint design.
15. The design lacked explicit concurrency/conflict analysis.
16. "All operations are synchronous" was asserted without workload evidence.
