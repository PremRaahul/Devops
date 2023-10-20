FROM node:18-alpine
RUN addgroup app && adduser -S -G app app
USER app
WORKDIR /app
COPY --chown=app:app package*.json .
RUN npm install
COPY --chown=app:app . .
ENV API_URL=http://api/apiurl.com/
EXPOSE 3000
CMD ["npm", "start"]