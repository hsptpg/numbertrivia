FROM microsoft/aspnetcore-build:2.0 AS build-env

WORKDIR /src
COPY web web

WORKDIR /src/web
RUN dotnet publish -c Release -o /app/out

# Build runtime image
FROM microsoft/aspnetcore:2.0
WORKDIR /app
COPY --from=build-env /app/out .

ENV ASPNETCORE_URLS http://+:8080
ENV ASPNETCORE_ENVIRONMENT Development
EXPOSE 8080

ENTRYPOINT ["dotnet", "web.dll"]